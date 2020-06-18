<script>
  import { goto } from "@sapper/app";

  import LoginSignUpPageContainer from "../containers/LoginSignUpPageContainer/index.svelte";
  import SharedInput from "../components/shared/SharedInput/index.svelte";
  import SharedCheckbox from "../components/shared/SharedCheckbox/index.svelte";
  import SharedButton from "../components/shared/SharedButton/index.svelte";
  import api from "../services";

  import { emailValidator, passwordValidator } from "../utils/validators.js";

  let email = "";
  let password = "";
  let isLoading = false;

  $: validatorEmail = emailValidator(email);
  $: validatorPassword = passwordValidator(password);

  const onChangeEmail = event => {
    const { value } = event;

    email = value;
  };

  const onChangePassword = event => {
    const { value } = event;
    password = value;
  };

  const handleOnSubmit = async () => {
    isLoading = true;
    const response = await api.loginUserApi(email, password);
    isLoading = false;

    if (response.success) {
      goto("/");
    }
  };

  $: isValidFormData = validatorEmail.isValid && validatorPassword.isValid;
</script>

<style>
  .form-heading {
    font-size: 32px;
    font-weight: bold;
    margin-bottom: 40px;
  }

  .login-button {
    padding-top: 20px;
  }
</style>

<svelte:head>
  <title>My store - Login</title>
</svelte:head>

<LoginSignUpPageContainer reverse={false}>
  <img slot="image" src={'/images/signin-image.jpg'} alt="login-img" />

  <a slot="change-link" href="/register">Create an account</a>

  <form slot="main-form" on:submit|preventDefault>
    <div class="form-heading">Sign in</div>

    <SharedInput
      type="text"
      name="email"
      label="Email"
      value={email}
      onChange={onChangeEmail}
      placeholder="Enter Email"
      error={validatorEmail.errorMessage} />

    <SharedInput
      type="password"
      name="password"
      label="Password"
      value={password}
      onChange={onChangePassword}
      placeholder="Enter Password"
      error={validatorPassword.errorMessage} />

    <div class="login-button">
      <SharedButton
        label="Log in"
        name="login-button"
        isDisabled={!isValidFormData}
        {isLoading}
        on:click={handleOnSubmit} />
    </div>
  </form>
</LoginSignUpPageContainer>
