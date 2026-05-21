# DmTribunal
<!DOCTYPE html>
<html lang="fr">

<head>
	<meta charset="UTF-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />

	<title>DM Tribunal</title>

	<style>
		* {
			margin: 0;
			padding: 0;
			box-sizing: border-box;
			font-family: Arial, Helvetica, sans-serif;
		}

		body {
			background: #050507;
			color: white;
			overflow-x: hidden;
		}

		body::before {
			content: "";
			position: fixed;
			inset: 0;
			background:
				radial-gradient(circle at top left, #ff2f92 0%, transparent 30%),
				radial-gradient(circle at bottom right, #8f2fff 0%, transparent 30%);
			opacity: 0.15;
			z-index: -1;
		}

		header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 25px 8%;
		}

		.logo {
			color: #ff5eb5;
			font-size: 24px;
			font-weight: bold;
		}

		nav {
			display: flex;
			gap: 20px;
			align-items: center;
		}

		nav button {
			background: none;
			border: none;
			color: #ccc;
			cursor: pointer;
			font-size: 15px;
			transition: 0.3s;
		}

		nav button:hover {
			color: #ff5eb5;
		}

		.login-btn {
			background: linear-gradient(90deg, #ff4fa3, #ff73c7);
			color: white;
			border: none;
			padding: 12px 22px;
			border-radius: 30px;
			cursor: pointer;
			box-shadow: 0 0 20px rgba(255, 79, 163, 0.4);
		}

		.hero {
			min-height: 90vh;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 0 8%;
			gap: 60px;
		}

		.hero-text {
			max-width: 550px;
		}

		.tag {
			display: inline-block;
			padding: 8px 16px;
			border-radius: 20px;
			background: rgba(255, 255, 255, 0.05);
			color: #ff73c7;
			margin-bottom: 25px;
		}

		h1 {
			font-size: 72px;
			line-height: 1;
			margin-bottom: 25px;
		}

		h1 span {
			color: #ff5eb5;
		}

		.hero-text p {
			color: #aaa;
			line-height: 1.7;
			margin-bottom: 30px;
		}

		.main-btn {
			padding: 18px 32px;
			border: none;
			border-radius: 40px;
			background: linear-gradient(90deg, #ff4fa3, #ff73c7);
			color: white;
			cursor: pointer;
			font-size: 16px;
			box-shadow: 0 0 30px rgba(255, 79, 163, 0.4);
			transition: 0.3s;
		}

		.main-btn:hover {
			transform: translateY(-3px);
		}

		.phone {
			width: 350px;
			background: #0f0f14;
			border: 1px solid rgba(255, 255, 255, 0.08);
			border-radius: 35px;
			padding: 25px;
			box-shadow: 0 0 40px rgba(255, 79, 163, 0.15);
		}

		.chat {
			display: flex;
			flex-direction: column;
			gap: 14px;
			margin-bottom: 25px;
		}

		.message {
			padding: 14px;
			border-radius: 18px;
			max-width: 75%;
			font-size: 14px;
		}

		.left {
			align-self: flex-start;
			background: #1a1a22;
		}

		.right {
			align-self: flex-end;
			background: linear-gradient(90deg, #ff4fa3, #ff73c7);
		}

		textarea {
			width: 100%;
			height: 120px;
			background: #111118;
			border: 1px solid rgba(255, 255, 255, 0.08);
			border-radius: 16px;
			color: white;
			padding: 15px;
			resize: none;
			margin-bottom: 15px;
		}

		.analyze-btn {
			width: 100%;
			padding: 16px;
			border: none;
			border-radius: 18px;
			background: linear-gradient(90deg, #ff4fa3, #ff73c7);
			color: white;
			font-size: 15px;
			cursor: pointer;
		}

		.result {
			margin-top: 20px;
			padding: 20px;
			border-radius: 20px;
			background: rgba(255, 255, 255, 0.04);
			display: none;
		}

		.result h2 {
			margin-bottom: 10px;
			color: #ff73c7;
		}

		.cards-section {
			padding: 80px 8%;
		}

		.section-title {
			text-align: center;
			margin-bottom: 50px;
			font-size: 42px;
		}

		.cards {
			display: grid;
			grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
			gap: 25px;
		}

		.card {
			background: rgba(255, 255, 255, 0.03);
			border: 1px solid rgba(255, 255, 255, 0.08);
			border-radius: 25px;
			padding: 30px;
			transition: 0.3s;
		}

		.card:hover {
			transform: translateY(-6px);
			border-color: #ff5eb5;
		}

		.card h3 {
			margin-bottom: 15px;
		}

		.score {
			font-size: 50px;
			color: #ff5eb5;
			margin-bottom: 15px;
		}

		footer {
			padding: 40px;
			text-align: center;
			color: #666;
		}

		@media(max-width:950px) {

			.hero {
				flex-direction: column;
				text-align: center;
				padding-top: 30px;
			}

			h1 {
				font-size: 52px;
			}

			nav {
				display: none;
			}

		}
	</style>
</head>

<body>

	<header>

		<div class="logo">DM TRIBUNAL</div>

		<nav>
			<button onclick="showMessage('Accueil')">Accueil</button>
			<button onclick="showMessage('Exemples')">Exemples</button>
			<button onclick="showMessage('Classement')">Classement</button>
			<button onclick="showMessage('À propos')">À propos</button>

			<button class="login-btn" onclick="login()">
				Se connecter
			</button>
		</nav>

	</header>

	<section class="hero">

		<div class="hero-text">

			<div class="tag">
				⚖ Bienvenue au tribunal
			</div>

			<h1>
				Le tribunal<br>
				de tes <span>messages</span>
			</h1>

			<p>
				Colle une conversation et laisse notre IA
				analyser les vibes, les red flags et les signes d’intérêt.
			</p>

			<button class="main-btn" onclick="scrollToAnalyzer()">
				Soumettre une conversation
			</button>

		</div>

		<div class="phone">

			<div class="chat">

				<div class="message left">
					Salut toi 👀
				</div>

				<div class="message right">
					Heyy ça va ?
				</div>

				<div class="message left">
					Tu fais quoi ce soir ?
				</div>

				<div class="message right">
					Netflix 😭
				</div>

			</div>

			<textarea id="conversation" placeholder="Colle ici ta conversation..."></textarea>

			<button class="analyze-btn" onclick="analyzeConversation()">
				Analyser la conversation
			</button>

			<div class="result" id="result">
				<h2 id="verdict"></h2>
				<p id="analysis"></p>
			</div>

		</div>

	</section>

	<section class="cards-section">

		<h2 class="section-title">
			Verdicts possibles
		</h2>

		<div class="cards">

			<div class="card">
				<h3>🟢 Acquitté</h3>
				<div class="score">8.2</div>
				<p>
					Bonne conversation, énergie réciproque.
				</p>
			</div>

			<div class="card">
				<h3>🟠 Coupable</h3>
				<div class="score">4.6</div>
				<p>
					Réponses sèches et vibe étrange.
				</p>
			</div>

			<div class="card">
				<h3>🔴 Condamné</h3>
				<div class="score">1.8</div>
				<p>
					Red flags détectés immédiatement.
				</p>
			</div>

		</div>

	</section>

	<footer>
		© 2026 — DM Tribunal
	</footer>

	<script>
		function showMessage(page) {
			alert("Tu as cliqué sur : " + page);
		}

		function login() {
			alert("Système de connexion bientôt disponible 👀");
		}

		function scrollToAnalyzer() {
			document
				.getElementById("conversation")
				.scrollIntoView({
					behavior: "smooth"
				});
		}

		function analyzeConversation() {

			const text =
				document.getElementById("conversation").value;

			const result =
				document.getElementById("result");

			const verdict =
				document.getElementById("verdict");

			const analysis =
				document.getElementById("analysis");

			if (text.trim() === "") {

				verdict.innerHTML = "⚠️ Aucun message";

				analysis.innerHTML =
					"Tu dois coller une conversation avant l’analyse.";

				result.style.display = "block";

				return;
			}

			const positiveWords = [
				"mdr",
				"😂",
				"❤️",
				"🥰",
				"love",
				"viens",
				"ensemble",
				"beau",
				"belle",
				"😍"
			];

			let score = 0;

			positiveWords.forEach(word => {

				if (text.toLowerCase().includes(word)) {
					score++;
				}

			});

			if (score >= 4) {

				verdict.innerHTML = "🟢 ACQUITTÉ";

				analysis.innerHTML =
					"Très bonne vibe détectée. Intérêt mutuel probable. Continue comme ça 😌";

			} else if (score >= 2) {

				verdict.innerHTML = "🟠 COUPABLE";

				analysis.innerHTML =
					"Conversation mitigée. Quelques bons signes mais ça reste flou.";

			} else {

				verdict.innerHTML = "🔴 CONDAMNÉ";

				analysis.innerHTML =
					"Aïe... énergie froide détectée. Il faut sauver cette discussion 😭";

			}

			result.style.display = "block";
		}
	</script>

</body>

</html>