const form = document.getElementById("loginForm");
const email = document.getElementById("email");
const password = document.getElementById("password");
const error = document.getElementById("error");
const message = document.getElementById("message");
const submitBtn = document.getElementById("submitBtn");
const togglePassword = document.getElementById("togglePassword");

// Show error message
function showError(text) {
    error.textContent = text;
    error.classList.add("show");
    message.textContent = "";
}

// Clear messages
function clearStatus() {
    error.classList.remove("show");
    message.textContent = "";
}

// Show / hide password
togglePassword.addEventListener("click", () => {
    if (password.type === "password") {
        password.type = "text";
        togglePassword.textContent = "Hide";
    } else {
        password.type = "password";
        togglePassword.textContent = "Show";
    }
});

// Email sign-in
form.addEventListener("submit", (event) => {
    event.preventDefault();

    clearStatus();

    const emailValue = email.value.trim();
    const passwordValue = password.value;

    // Check email
    if (!emailValue || !emailValue.includes("@")) {
        showError("Please enter a valid email address.");
        email.focus();
        return;
    }

    // Check password
    if (!passwordValue) {
        showError("Please enter your password.");
        password.focus();
        return;
    }

    // Loading state
    submitBtn.disabled = true;
    submitBtn.textContent = "Signing in...";

    // Demo login
    setTimeout(() => {
        submitBtn.disabled = false;
        submitBtn.textContent = "Sign in with email";

        message.textContent = "Sign-in submitted successfully.";
    }, 900);
});

// Google login
document.getElementById("googleBtn").addEventListener("click", () => {
    clearStatus();
    message.textContent = "Google sign-in would open here.";
});

// Microsoft login
document.getElementById("microsoftBtn").addEventListener("click", () => {
    clearStatus();
    message.textContent = "Microsoft sign-in would open here.";
});

// Reset password
document.getElementById("resetPassword").addEventListener("click", (event) => {
    event.preventDefault();

    const emailValue = email.value.trim();

    if (!emailValue || !emailValue.includes("@")) {
        showError("Enter your email address first.");
        email.focus();
        return;
    }

    clearStatus();
    message.textContent =
        "Password reset instructions would be sent to your email.";
});

// Support chat
document.getElementById("chatBtn").addEventListener("click", () => {
    clearStatus();
    message.textContent = "Support chat opened.";
});# .-
