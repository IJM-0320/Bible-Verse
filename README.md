<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily Bible Verse</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 50px; }
        #verseBox { font-size: 24px; font-weight: bold; margin-top: 20px; }
    </style>
</head>
<body>

    <h1>Today's Bible Verse:</h1>
    <div id="verseBox">Loading...</div>

    <script>
        async function fetchBibleVerse() {
            try {
                const response = await fetch("https://dailyverses.net/random-bible-verse");
                const text = await response.text();
                
                // Extract the verse using DOM parsing
                let parser = new DOMParser();
                let doc = parser.parseFromString(text, 'text/html');
                let verse = doc.querySelector(".bibleVerse .text")?.innerText || "Verse not found";
                let reference = doc.querySelector(".bibleVerse .reference")?.innerText || "";

                document.getElementById("verseBox").innerText = verse + " (" + reference + ")";
            } catch (error) {
                document.getElementById("verseBox").innerText = "Error fetching verse.";
                console.error("Failed to fetch the Bible verse:", error);
            }
        }

        window.onload = fetchBibleVerse;
    </script>

</body>
</html>
