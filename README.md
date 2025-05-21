<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily Bible Verse</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 50px; }
        #verseBox { font-size: 20px; font-weight: bold; margin-top: 20px; }
    </style>
</head>
<body>

    <h2>Hi, Good Day! Here's your Bible verse for today:</h2>
    <div id="verseBox">Loading...</div>

    <script>
        const kjvBible = {
            "Genesis": {
                "1": {
                    "1": "In the beginning God created the heaven and the earth.",
                    "2": "And the earth was without form, and void..."
                },
                "2": {
                    "7": "And the LORD God formed man of the dust of the ground..."
                }
            },
            "Matthew": {
                "6": {
                    "33": "But seek ye first the kingdom of God, and his righteousness...",
                    "34": "Take therefore no thought for the morrow..."
                },
                "11": {
                    "28": "Come unto me, all ye that labour and are heavy laden..."
                }
            }
        };

        function getRandomVerse() {
            const books = Object.keys(kjvBible);
            const randomBook = books[Math.floor(Math.random() * books.length)];
            const chapters = Object.keys(kjvBible[randomBook]);
            const randomChapter = chapters[Math.floor(Math.random() * chapters.length)];
            const verses = Object.keys(kjvBible[randomBook][randomChapter]);
            const randomVerseNum = verses[Math.floor(Math.random() * verses.length)];
            const randomVerse = kjvBible[randomBook][randomChapter][randomVerseNum];

            document.getElementById("verseBox").innerText = `${randomBook} ${randomChapter}:${randomVerseNum} - ${randomVerse}`;
        }

        window.onload = getRandomVerse;
    </script>

</body>
</html>
