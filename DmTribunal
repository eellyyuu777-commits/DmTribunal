<!--
VRAI TEMPLATE FULL APP
Frontend + Auth + Sauvegarde + Multi conversations
TOUT fonctionne réellement côté navigateur.

⚠️ Pour avoir un vrai système mondial en ligne :
tu devras connecter Supabase/Firebase plus tard.

Mais CE code :
- fonctionne vraiment
- sauvegarde vraiment
- crée vraiment des comptes localement
- gère plusieurs conversations
- upload des images
- dashboard dynamique
- historique réel
-->

<!DOCTYPE html>
<html lang="fr">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>DM Tribunal</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial, sans-serif;
}

body{
background:#07070b;
color:white;
overflow-x:hidden;
}

body::before{
content:"";
position:fixed;
inset:0;

background:
radial-gradient(circle at top left,#ff2f92 0%,transparent 30%),
radial-gradient(circle at bottom right,#7b2fff 0%,transparent 30%);

opacity:0.15;
z-index:-1;
}

header{
display:flex;
justify-content:space-between;
align-items:center;
padding:25px 8%;
}

.logo{
font-size:24px;
font-weight:bold;
color:#ff5eb5;
}

nav{
display:flex;
gap:15px;
align-items:center;
}

nav button{
background:none;
border:none;
color:#ccc;
cursor:pointer;
font-size:15px;
}

nav button:hover{
color:#ff5eb5;
}

.main-btn{
background:linear-gradient(90deg,#ff4fa3,#ff73c7);
border:none;
padding:14px 24px;
border-radius:30px;
color:white;
cursor:pointer;
}

.hero{
padding:80px 8%;
display:flex;
justify-content:space-between;
align-items:flex-start;
gap:50px;
}

.left{
max-width:550px;
}

.left h1{
font-size:70px;
line-height:1;
margin-bottom:25px;
}

.left span{
color:#ff5eb5;
}

.left p{
color:#aaa;
line-height:1.7;
margin-bottom:30px;
}

.panel{
width:430px;
background:#111118;
border:1px solid rgba(255,255,255,0.08);
border-radius:25px;
padding:25px;
}

textarea{
width:100%;
height:140px;
background:#1a1a22;
border:none;
border-radius:16px;
padding:15px;
color:white;
resize:none;
margin-bottom:15px;
}

input{
width:100%;
padding:15px;
background:#1a1a22;
border:none;
border-radius:16px;
margin-bottom:15px;
color:white;
}

.result{
margin-top:20px;
background:rgba(255,255,255,0.05);
padding:20px;
border-radius:18px;
display:none;
}

.result h2{
margin-bottom:10px;
}

.upload{
background:#1a1a22;
padding:18px;
border-radius:16px;
margin-bottom:15px;
}

.preview{
width:100%;
border-radius:15px;
margin-top:15px;
display:none;
}

.dashboard{
padding:70px 8%;
}

.cards{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
gap:20px;
margin-top:30px;
}

.card{
background:rgba(255,255,255,0.04);
border:1px solid rgba(255,255,255,0.08);
border-radius:20px;
padding:25px;
}

.card h3{
margin-bottom:15px;
color:#ff5eb5;
}

.small{
font-size:14px;
color:#888;
margin-top:15px;
}

.auth{
position:fixed;
inset:0;
background:rgba(0,0,0,0.85);
display:none;
justify-content:center;
align-items:center;
z-index:999;
}

.auth-box{
width:400px;
background:#111118;
padding:30px;
border-radius:25px;
}

.auth-box h2{
margin-bottom:20px;
}

.close{
background:#222;
margin-top:10px;
width:100%;
}

.user-info{
padding:15px 8%;
color:#ff73c7;
}

@media(max-width:950px){

.hero{
flex-direction:column;
}

.left h1{
font-size:50px;
}

.panel{
width:100%;
}

}

</style>
</head>

<body>

<header>

<div class="logo">
DM TRIBUNAL
</div>

<nav>

<button onclick="scrollToSection('home')">
Accueil
</button>

<button onclick="scrollToSection('dashboard')">
Dashboard
</button>

<button onclick="openAuth()">
Connexion
</button>

<button class="main-btn" onclick="logout()">
Déconnexion
</button>

</nav>

</header>

<div class="user-info" id="userInfo">
Non connecté
</div>

<section class="hero" id="home">

<div class="left">

<h1>
Le tribunal de tes
<span>messages</span>
</h1>

<p>
Analyse des conversations, upload de captures,
historique complet et dashboard personnel.
</p>

<button class="main-btn" onclick="scrollToSection('analyzer')">
Commencer
</button>

</div>

<div class="panel" id="analyzer">

<h2 style="margin-bottom:20px;">
Nouvelle conversation
</h2>

<textarea
id="conversation"
placeholder="Colle une conversation ici..."
></textarea>

<div class="upload">

<p style="margin-bottom:10px;">
Ajouter une capture d'écran
</p>

<input
type="file"
accept="image/*"
onchange="previewImage(event)"
>

<img id="preview" class="preview">

</div>

<button
class="main-btn"
style="width:100%;"
onclick="analyzeConversation()"
>
Analyser
</button>

<div class="result" id="result">

<h2 id="verdict"></h2>

<p id="analysis"></p>

</div>

</div>

</section>

<section class="dashboard" id="dashboard">

<h2>
Historique des analyses
</h2>

<div class="cards" id="history">

</div>

</section>

<div class="auth" id="auth">

<div class="auth-box">

<h2>
Connexion / Inscription
</h2>

<input
type="text"
id="username"
placeholder="Nom d'utilisateur"
>

<input
type="password"
id="password"
placeholder="Mot de passe"
>

<button
class="main-btn"
style="width:100%;"
onclick="register()"
>
Créer un compte
</button>

<button
class="main-btn"
style="width:100%; margin-top:10px;"
onclick="login()"
>
Connexion
</button>

<button
class="main-btn close"
onclick="closeAuth()"
>
Fermer
</button>

</div>

</div>

<script>

let currentUser = null;

function openAuth(){

document.getElementById("auth").style.display = "flex";

}

function closeAuth(){

document.getElementById("auth").style.display = "none";

}

function scrollToSection(id){

document
.getElementById(id)
.scrollIntoView({
behavior:"smooth"
});

}

function updateUserDisplay(){

const userInfo =
document.getElementById("userInfo");

if(currentUser){

userInfo.innerHTML =
"Connecté en tant que : " + currentUser;

}

else{

userInfo.innerHTML =
"Non connecté";

}

}

function register(){

const username =
document.getElementById("username").value;

const password =
document.getElementById("password").value;

if(username === "" || password === ""){

alert("Remplis tous les champs");

return;

}

const users =
JSON.parse(localStorage.getItem("users")) || [];

const alreadyExists =
users.find(user => user.username === username);

if(alreadyExists){

alert("Compte déjà existant");

return;

}

users.push({
username,
password
});

localStorage.setItem(
"users",
JSON.stringify(users)
);

alert("Compte créé");

}

function login(){

const username =
document.getElementById("username").value;

const password =
document.getElementById("password").value;

const users =
JSON.parse(localStorage.getItem("users")) || [];

const user =
users.find(
u =>
u.username === username &&
u.password === password
);

if(!user){

alert("Identifiants incorrects");

return;

}

currentUser = username;

localStorage.setItem(
"currentUser",
username
);

updateUserDisplay();

loadHistory();

closeAuth();

}

function logout(){

currentUser = null;

localStorage.removeItem("currentUser");

updateUserDisplay();

alert("Déconnecté");

}

function previewImage(event){

const file = event.target.files[0];

if(!file) return;

const preview =
document.getElementById("preview");

preview.src =
URL.createObjectURL(file);

preview.style.display = "block";

}

function analyzeConversation(){

if(!currentUser){

alert("Connecte-toi avant");

return;

}

const text =
document.getElementById("conversation").value;

if(text.trim() === ""){

alert("Ajoute une conversation");

return;

}

const positiveWords = [
"❤️",
"🥰",
"love",
"viens",
"ensemble",
"😍",
"beau",
"belle",
"mdr"
];

let score = 0;

positiveWords.forEach(word => {

if(text.toLowerCase().includes(word)){

score++;

}

});

let verdict = "";
let analysis = "";

if(score >= 4){

verdict = "🟢 ACQUITTÉ";

analysis =
"Très bonne vibe détectée.";

}

else if(score >= 2){

verdict = "🟠 COUPABLE";

analysis =
"Conversation mitigée.";

}

else{

verdict = "🔴 CONDAMNÉ";

analysis =
"Red flags détectés.";

}

document.getElementById("result").style.display =
"block";

document.getElementById("verdict").innerHTML =
verdict;

document.getElementById("analysis").innerHTML =
analysis;

saveConversation(
text,
verdict,
analysis
);

}

function saveConversation(
text,
verdict,
analysis
){

const allConversations =
JSON.parse(
localStorage.getItem("conversations")
) || [];

allConversations.push({

user:currentUser,
text,
verdict,
analysis,
date:new Date().toLocaleString()

});

localStorage.setItem(
"conversations",
JSON.stringify(allConversations)
);

loadHistory();

}

function loadHistory(){

const history =
JSON.parse(
localStorage.getItem("conversations")
) || [];

const container =
document.getElementById("history");

container.innerHTML = "";

const filtered =
history.filter(
item => item.user === currentUser
);

filtered.reverse().forEach(item => {

container.innerHTML += `

<div class="card">

<h3>
${item.verdict}
</h3>

<p>
${item.analysis}
</p>

<div class="small">

${item.date}

<br><br>

${item.text.substring(0,120)}...

</div>

</div>

`;

});

}

window.onload = () => {

const savedUser =
localStorage.getItem("currentUser");

if(savedUser){

currentUser = savedUser;

updateUserDisplay();

loadHistory();

}

};

</script>

</body>

</html>