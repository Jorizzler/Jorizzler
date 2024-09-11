<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Escape Room</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        .container {
            margin: 50px;
        }
        .question {
            font-size: 24px;
            margin-bottom: 20px;
        }
        img {
            width: 150px;
            height: auto;
            cursor: pointer;
            margin: 10px;
        }
        .hidden {
            display: none;
        }
        .message {
            font-size: 20px;
            color: green;
        }
        .name-option {
            cursor: pointer;
            margin: 10px;
            font-size: 20px;
        }
        .input-container {
            margin: 20px 0;
        }
        .input-container input {
            font-size: 20px;
            padding: 10px;
            width: 100px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Escape Room: Finde die richtige Antwort!</h1>
        
        <!-- Level 1: Seilbahnteile -->
        <div id="level1">
            <p class="question">Dein Vater sagt: „Dieses Teil hält die Kabine sicher am Seil fest.“</p>
            <img src="klemme.jpg" alt="Klemme" onclick="checkAnswer(1, true)">
            <img src="antriebsmotor.jpg" alt="Antriebsmotor" onclick="checkAnswer(1, false)">
            <img src="umlenkscheibe.jpg" alt="Umlenkscheibe" onclick="checkAnswer(1, false)">
            <p id="message1" class="message hidden">Richtig! Weiter zum nächsten Level...</p>
        </div>

        <!-- Level 2: Namen-Rätsel -->
        <div id="level2" class="hidden">
            <p class="question">Wähle den richtigen Namen:</p>
            <span class="name-option" onclick="checkName('Serge', true)">Serge</span>
            <span class="name-option" onclick="checkName('Max', false)">Max</span>
            <span class="name-option" onclick="checkName('Paul', false)">Paul</span>
            <span class="name-option" onclick="checkName('Lucas', false)">Lucas</span>
            <p id="message2" class="message hidden">Richtig! Weiter zum nächsten Level...</p>
        </div>

        <!-- Level 3: Taekwondo-Rätsel -->
        <div id="level3" class="hidden">
            <p class="question">Gib die richtige Reihenfolge der Taekwondo-Übungen ein:</p>
            <div class="input-container">
                <input type="text" id="codeInput" placeholder="Code eingeben">
                <button onclick="checkTaekwondoCode()">Überprüfen</button>
            </div>
            <p id="message3" class="message hidden">Herzlichen Glückwunsch, du hast alle Level abgeschlossen!</p>
        </div>
    </div>

    <script>
        // Level 1: Seilbahnteile
        function checkAnswer(level, isCorrect) {
            if (isCorrect) {
                document.getElementById('message' + level).classList.remove('hidden');
                setTimeout(function() {
                    document.getElementById('level' + level).classList.add('hidden');
                    if (level < 3) {
                        document.getElementById('level' + (level + 1)).classList.remove('hidden');
                    }
                }, 2000);
            } else {
                alert("Das ist leider falsch. Versuche es nochmal!");
            }
        }

        // Level 2: Namen-Rätsel
        function checkName(selectedName, isCorrect) {
            if (isCorrect) {
                document.getElementById('message2').classList.remove('hidden');
                setTimeout(function() {
                    document.getElementById('level2').classList.add('hidden');
                    document.getElementById('level3').classList.remove('hidden');
                }, 2000);
            } else {
                alert("Das ist leider falsch. Versuche es nochmal!");
            }
        }

        // Level 3: Taekwondo-Rätsel
        const correctCode = '1,4,7,2,5,6'; // Beispiel-Code, den dein Vater vorgibt

        function checkTaekwondoCode() {
            const userCode = document.getElementById('codeInput').value;
            if (userCode === correctCode) {
                document.getElementById('message3').classList.remove('hidden');
                setTimeout(function() {
                    alert('Herzlichen Glückwunsch! Du hast alle Rätsel erfolgreich gelöst.');
                }, 2000);
            } else {
                alert("Der Code ist leider falsch. Versuche es nochmal!");
            }
        }
    </script>
</body>
</html>
