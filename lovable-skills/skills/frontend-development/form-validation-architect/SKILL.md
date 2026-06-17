---
name: form-validation-architect
description: Use when building forms — simple contact forms, complex multi-step wizards, real-time validation. Always uses react-hook-form + Zod, with accessible error handling and submission states.
---

# Form Validation Architect

Forms are the #1 source of UX pain. Build them right.

## Stack
- `react-hook-form` — performant, controlled or uncontrolled
- `zod` — schema validation, type inference
- `@hookform/resolvers` — bridges RHF + Zod

## Basic Form Pattern
```tsx
const schema = z.object({
  email: z.string().email('Enter a valid email'),
  password: z.string().min(8, 'At least 8 characters'),
})
type FormData = z.infer<typeof schema>

const { register, handleSubmit, formState: { errors, isSubmitting } } = useForm<FormData>({
  resolver: zodResolver(schema),
})

const onSubmit = async (data: FormData) => {
  // submission
}

return (
  <form onSubmit={handleSubmit(onSubmit)} noValidate>
    <Field label="Email" error={errors.email?.message}>
      <input
        {...register('email')}
        type="email"
        aria-invalid={!!errors.email}
      />
    </Field>
    <Field label="Password" error={errors.password?.message}>
      <input
        {...register('password')}
        type="password"
        aria-invalid={!!errors.password}
      />
    </Field>
    <Button type="submit" isLoading={isSubmitting}>Submit</Button>
  </form>
)
```

## Validation Strategies
- **On blur**: validate when the user leaves the field (default RHF mode: `onSubmit` then `onChange`)
- **On submit**: validate only when the user submits (less annoying)
- **On change**: validate as they type (most responsive, most annoying)
- **Recommended**: `mode: 'onBlur'` + `reValidateMode: 'onChange'`

## Accessibility Rules
- Every input has a `<label>` (not placeholder-as-label)
- Errors are linked with `aria-describedby`
- Invalid fields have `aria-invalid="true"`
- Error messages are announced (use `role="alert"`)
- Required fields marked with `aria-required="true"` and visual `*`

## Field Component
```tsx
function Field({ label, error, required, children, htmlFor }) {
  return (
    <div className="space-y-1.5">
      <label htmlFor={htmlFor} className="text-sm font-medium">
        {label}
        {required && <span className="text-destructive ml-0.5">*</span>}
      </label>
      {children}
      {error && (
        <p id={`${htmlFor}-error`} role="alert" className="text-sm text-destructive">
          {error}
        </p>
      )}
    </div>
  )
}
```

## Multi-Step Wizard
```tsx
const [step, setStep] = useState(0)
const steps = ['account', 'profile', 'preferences', 'confirm']

const form = useForm<FormData>({ resolver: zodResolver(schema), mode: 'onBlur' })

const next = async () => {
  const valid = await form.trigger(steps[step])
  if (valid) setStep(s => s + 1)
}
```

## Common Schema Patterns
```ts
// Password strength
z.string()
  .min(8, 'At least 8 characters')
  .regex(/[A-Z]/, 'Must contain uppercase')
  .regex(/[0-9]/, 'Must contain a number')

// Phone (flexible)
z.string().regex(/^\+?[\d\s-()]+$/, 'Invalid phone')

// URL
z.string().url('Must be a valid URL')

// Date range
z.object({
  start: z.coerce.date(),
  end: z.coerce.date(),
}).refine(d => d.end > d.start, { message: 'End must be after start', path: ['end'] })

// Conditional
z.object({
  hasCompany: z.boolean(),
  companyName: z.string().optional(),
}).refine(d => !d.hasCompany || d.companyName, {
  message: 'Company name required',
  path: ['companyName'],
})
```

## Submission States
- Idle: button enabled, no spinner
- Submitting: button disabled, spinner shown, `aria-busy="true"` on form
- Success: show success message, reset form
- Error: show error message, keep form data, focus the error

## Forbidden Patterns
- Controlled inputs without RHF (re-renders the whole form on every keystroke)
- Placeholder as label
- Inline error messages without `aria-describedby`
- Disabling submit until valid (let users try and see errors)
- `any` types — Zod schemas should infer types

## Output Format
1. Schema definition
2. Form component
3. Field component
4. Submission states
5. Accessibility checklist

