<script>
  import { useForm, Validators } from "svelte-use-form";
  const form = useForm({
    email: { validators: [Validators.email, Validators.required] },
    password: { validators: [Validators.required] },
  });
</script>

<form use:form>
  <h1>Login</h1>
  <input type="email" name="email" />
  <div class="error">
    {#if $form.email.touched}
      {#if $form.email.errors.required}
        This is a mandatory field
      {:else if $form.email.errors.email}
        Email is not valid
      {/if}
    {/if}
  </div>

  <input type="password" name="password" />
  <div class="error">
    {#if $form.password.touched && $form.password.errors.required}
      This is a mandatory field
    {/if}
  </div>
  <button disabled={!$form.valid}>Login</button>
</form>
