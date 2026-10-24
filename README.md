# register-and-name
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Регистрация и вход</title>
<style>
*{box-sizing:border-box}
body{margin:0;min-height:100vh;display:grid;place-items:center;padding:20px;font-family:Arial,sans-serif;background:linear-gradient(135deg,#111827,#312e81,#6d28d9)}
.card{width:100%;max-width:390px;padding:32px;background:#fff;border-radius:22px;box-shadow:0 20px 70px #0005}
h1{text-align:center;color:#1e1b4b;margin-bottom:8px}
.subtitle{text-align:center;color:#777;margin-bottom:25px}
label{display:block;margin:15px 0 7px;font-size:14px}
input{width:100%;padding:13px;border:1px solid #ddd;border-radius:9px;font-size:15px;outline:none}
input:focus{border-color:#6d28d9}
button{width:100%;padding:13px;margin-top:22px;border:0;border-radius:9px;background:#6d28d9;color:white;font-size:15px;cursor:pointer}
button:hover{background:#5b21b6}
.switch{text-align:center;font-size:14px;margin-top:20px;color:#666}
.switch a{color:#6d28d9;cursor:pointer;font-weight:bold}
#message{text-align:center;font-size:14px;margin-top:15px}
</style>
</head>
<body>
<div class="card">
  <h1 id="heading">Создать аккаунт</h1>
  <p class="subtitle" id="subtitle">Зарегистрируйся, чтобы продолжить</p>
  <form id="form">
    <div id="nameField">
      <label for="name">Твоё имя</label>
      <input id="name" type="text" placeholder="Твоё имя" autocomplete="name" required>
    </div>
    <label for="email">Электронная почта</label>
    <input id="email" type="email" placeholder="you@example.com" autocomplete="email" required>
    <label for="password">Пароль</label>
    <input id="password" type="password" placeholder="Минимум 8 символов" minlength="8" autocomplete="current-password" required>
    <button id="submit" type="submit">Зарегистрироваться</button>
  </form>
  <p id="message" role="status"></p>
  <div class="switch"><span id="switchText">Уже есть аккаунт?</span> <a id="switchButton" href="#">Войти</a></div>
</div>
<script>
let isLogin = false;
const form = document.getElementById("form");
const nameField = document.getElementById("nameField");
const nameInput = document.getElementById("name");
const heading = document.getElementById("heading");
const subtitle = document.getElementById("subtitle");
const submit = document.getElementById("submit");
const switchText = document.getElementById("switchText");
const switchButton = document.getElementById("switchButton");
const message = document.getElementById("message");
switchButton.addEventListener("click", (event) => {
  event.preventDefault();
  isLogin = !isLogin;
  nameField.hidden = isLogin;
  nameInput.required = !isLogin;
  heading.textContent = isLogin ? "С возвращением!" : "Создать аккаунт";
  subtitle.textContent = isLogin ? "Войди в свой аккаунт" : "Зарегистрируйся, чтобы продолжить";
  submit.textContent = isLogin ? "Войти" : "Зарегистрироваться";
  switchText.textContent = isLogin ? "Нет аккаунта?" : "Уже есть аккаунт?";
  switchButton.textContent = isLogin ? "Регистрация" : "Войти";
  message.textContent = "";
});
form.addEventListener("submit", (event) => {
  event.preventDefault();
  if (!form.reportValidity()) return;
  message.style.color = "#6d28d9";
  message.textContent = isLogin ? "Демонстрация: для настоящего входа нужен сервер." : "Форма заполнена! Для создания аккаунта нужен сервер.";
});
</script>
</body>
</html>
