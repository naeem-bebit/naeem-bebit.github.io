---
title: "Contact"
url: /contact/
---

Have a question about data science, machine learning, or image processing? Send me a message below — I'll get back to you as soon as I can. :)

<form name="contact" class="contact-form" id="contact-form" method="POST" action="https://formspree.io/xayozngg">
  <p>
    <label>Your Name: <input type="text" name="name" autocomplete="name" required /></label>
  </p>
  <p>
    <label>Your Email: <input type="email" name="email" autocomplete="email" required /></label>
  </p>
  <p>
    <label>Subject: <input type="text" name="subject" /></label>
  </p>
  <p>
    <label>Message: <textarea name="message" required></textarea></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
  <p id="contact-status" class="contact-status" role="status" aria-live="polite"></p>
    <input type="hidden" name="_next" value="https://naeem-bebit.github.io/thankyou.html"/>
    <input type="text" name="_gotcha" style="display:none" />
</form>

<script>
(function () {
  var form = document.getElementById("contact-form");
  var status = document.getElementById("contact-status");
  form.addEventListener("submit", function (e) {
    e.preventDefault();
    var btn = form.querySelector('button[type="submit"]');
    btn.disabled = true;
    status.textContent = "Sending...";
    fetch("https://formspree.io/f/xayozngg", {
      method: "POST",
      body: new FormData(form),
      headers: { "Accept": "application/json" }
    }).then(function (res) {
      if (res.ok) {
        status.textContent = "Thanks! Your message has been sent.";
        form.reset();
      } else {
        status.textContent = "Something went wrong - please try again or email me directly.";
      }
    }).catch(function () {
      status.textContent = "Something went wrong - please try again or email me directly.";
    }).finally(function () {
      btn.disabled = false;
    });
  });
})();
</script>
