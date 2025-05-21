<!HI html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Bible Verse</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 50px; }
        #verseBox { font-size: 24px; font-weight: bold; margin-top: 20px; }
    </style>
</head>
<body>

    <h1>Welcome! Your Bible Verse for Today:</h1>
    <div id="verseBox">Loading...</div>

    <script>
        async function fetchRandomVerse() {
            try {
                const response = await fetch("https://raw.githubusercontent.com/thiagobodruk/bible/master/json/en_kjv.json");
                const data = await response.json();
                
                const books = Object.keys(data);
                const randomBook = books[Math.floor(Math.random() * books.length)];
                const chapters = Object.keys(data[randomBook]);
                const randomChapter = chapters[Math.floor(Math.random() * chapters.length)];
                const verses = Object.values(data[randomBook][randomChapter]);
                const randomVerse = verses[Math.floor(Math.random() * verses.length)];

                document.getElementById("verseBox").innerText = `${randomBook} ${randomChapter}: ${randomVerse}`;
            } catch (error) {
                document.getElementById("verseBox").innerText = "Error loading verse.";
                console.error("Failed to fetch Bible verses:", error);
            }
        }

        window.onload = fetchRandomVerse;
    </script>

</body>
</html>
