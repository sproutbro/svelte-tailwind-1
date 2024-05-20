<script>
    import { SignIn } from "@auth/sveltekit/components"
  </script>
   
<div>
    <nav>
      <img src="./logo.png" alt="Company Logo" />
      <SignIn provider="resend" />
    </nav>
</div>