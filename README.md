<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>cliquegagne</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #ffecd2, #fcb69f);
      text-align: center;
      padding: 30px;
      color: #2c3e50;
    }
    h1 {
      font-size: 2.5em;
      color: #d35400;
    }
    p {
      font-size: 1.1em;
      margin: 10px;
    }
    .container {
      background-color: #ffffffdd;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 600px;
      margin: 20px auto;
    }
    .share-btn {
      display: inline-block;
      margin: 15px auto;
      padding: 14px 28px;
      background-color: #e74c3c;
      color: white;
      text-decoration: none;
      font-size: 18px;
      border-radius: 50px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      transition: all 0.3s ease-in-out;
    }
    .share-btn:hover {
      background-color: #c0392b;
      transform: scale(1.05);
    }
    input[type="tel"] {
      padding: 10px;
      margin-top: 10px;
      width: 250px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 20px;
      margin-top: 20px;
      font-size: 16px;
      border: none;
      background-color: #28a745;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    #compteur {
      font-size: 1.2em;
      color: #16a085;
      font-weight: bold;
      margin-top: 10px;
    }
    .testimonial, #auto-msg {
      background-color: #ffffffcc;
      padding: 15px;
      border-radius: 10px;
      margin: 10px auto;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 500px;
    }
    ul.gifts {
      list-style: none;
      padding: 0;
    }
    ul.gifts li {
      background: #fff8;
      padding: 10px;
      border-radius: 10px;
      margin: 5px auto;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
      max-width: 500px;
    }
  </style>
</head>
<body>

  <audio id="bg-music" autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
  </audio>

  <audio id="success-sound">
    <source src="https://assets.mixkit.co/sfx/preview/mixkit-achievement-bell-600.mp3" type="audio/mp3">
  </audio>

  <div class="container">
    <h1>Bienvenue sur cliquegagne</h1>
    <p>Partage à <strong>15 amis</strong> et <strong>5 groupes</strong> pour débloquer tes Méga.</p>
    <p><strong>100 Mo</strong> gagnés à chaque ami invité.</p>
    <a class="share-btn" href="https://wa.me/?text=J’ai%20reçu%20mes%20Méga%20ici%20:%20https://capitaine39.github.io/cliquegagne/" onclick="incrementerCompteur();">Partager sur WhatsApp</a>
    <div id="compteur">Tu as partagé à 0 amis. Encore 15 !</div>

    <form id="form-telephone">
      <label for="telephone">Entrez votre numéro pour recevoir vos Méga :</label><br>
      <input type="tel" id="telephone" name="telephone" placeholder="ex: 0977409724" required>
    </form>
    <button onclick="playSuccess()">J'ai partagé</button>

    <h2>Cadeaux Bonus</h2>
    <ul class="gifts">
      <li>+500 Mo après 10 partages</li>
      <li>+1 Go si tu partages à 10 groupes</li>
      <li>Tirage au sort : un smartphone à gagner</li>
    </ul>

    <h2>Avis des utilisateurs</h2>
    <div class="testimonial"><strong>Fatou D.</strong> : Merci beaucoup ! J’ai reçu 1 Go après avoir partagé !</div>
    <div class="testimonial"><strong>Yannick T.</strong> : Je croyais que c’était faux, mais j’ai vraiment gagné un bonus !</div>
    <div class="testimonial"><strong>Aline M.</strong> : Grâce à ce site, je ne manque plus jamais de Méga !</div>
    <div class="testimonial" id="auto-msg"></div>

    <p style="margin-top: 20px;">Après avoir partagé, ferme la page. Tes Méga arrivent bientôt !</p>
  </div>

  <script>
    let partages = 0;
    function incrementerCompteur() {
      partages++;
      let restant = 15 - partages;
      if (restant > 0) {
        document.getElementById("compteur").innerText =
          `Tu as partagé à ${partages} amis. Encore ${restant} pour débloquer tes Méga !`;
      } else {
        document.getElementById("compteur").innerText =
          `Bravo ! Tu as débloqué tes Méga !`;
        document.getElementById("success-sound").play();
      }
    }

    function playSuccess() {
      document.getElementById("success-sound").play();
      alert("Merci pour ton partage ! Tu recevras tes Méga bientôt.");
    }

    const messages = [
      "À chaque fois je réussis mes Méga grâce à ce site.",
      "Encore une fois, j’ai reçu mes Mo, c’est incroyable !",
      "Merci à ce site, je ne reste jamais sans connexion.",
      "Ce site fonctionne vraiment, je le recommande à tous.",
      "J’ai eu mes Méga comme promis, trop fort !",
      "Franchement, ça marche à chaque fois ! Merci !"
    ];
    let index = 0;
    function afficherMessage() {
      const el = document.getElementById("auto-msg");
      el.textContent = messages[index];
      index = (index + 1) % messages.length;
    }
    setInterval(afficherMessage, 4000);
    afficherMessage();
  </script>
</body>
</html>
