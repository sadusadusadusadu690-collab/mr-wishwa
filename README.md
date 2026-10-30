<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>MR WISHWA | Free Fire Videos</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background: #101010;
    color: white;
}

header {
    background: #e60023;
    padding: 20px;
    display: flex;
    align-items: center;
    gap: 15px;
}

.logo {
    background: #111;
    color: red;
    border: 2px solid white;
    padding: 12px;
    font-size: 20px;
    font-weight: bold;
    border-radius: 10px;
}

header h1 {
    font-size: 27px;
}

header p {
    font-size: 12px;
    margin-top: 5px;
}

.hero {
    text-align: center;
    padding: 35px 15px;
    background: linear-gradient(135deg, #310008, #151515);
}

.hero h2 {
    color: #ff233f;
    margin-bottom: 12px;
}

button {
    border: none;
    padding: 12px 18px;
    border-radius: 7px;
    background: #e60023;
    color: white;
    font-weight: bold;
    cursor: pointer;
    margin: 8px 4px;
}

button:hover {
    background: #ff334d;
}

.upload-box {
    max-width: 500px;
    margin: 25px auto;
    padding: 20px;
    background: #1c1c1c;
    border: 1px solid #333;
    border-radius: 12px;
}

input {
    width: 100%;
    padding: 12px;
    margin: 10px 0;
    background: #292929;
    color: white;
    border: 1px solid #555;
    border-radius: 6px;
}

h2.section-title {
    text-align: center;
    margin: 30px 0 20px;
    color: #ff233f;
}

.video-grid {
    display: grid;
    grid-template-columns:
        repeat(auto-fit, minmax(230px, 1fr));
    gap: 18px;
    padding: 20px;
}

.video-card {
    background: #1c1c1c;
    border: 1px solid #333;
    border-radius: 12px;
    overflow: hidden;
}

video {
    width: 100%;
    display: block;
    background: black;
}

.video-info {
    padding: 15px;
}

.video-info h3 {
    margin-bottom: 8px;
    overflow-wrap: anywhere;
}

.video-info a {
    display: inline-block;
    padding: 10px;
    margin-top: 10px;
    background: #e60023;
    color: white;
    text-decoration: none;
    border-radius: 6px;
}

.delete-btn {
    background: #444;
}

footer {
    text-align: center;
    padding: 25px;
    margin-top: 30px;
    background: #080808;
    color: #aaa;
}
</style>
</head>

<body>

<header>
    <div class="logo">MR W</div>

    <div>
        <h1>MR WISHWA</h1>
        <p>FREE FIRE VIDEO DOWNLOAD</p>
    </div>
</header>

<section class="hero">
    <h2>🔥 FREE FIRE VIDEOS 🔥</h2>

    <p>
        Watch and download Free Fire gameplay videos!
    </p>

    <button onclick="showUpload()">
        + Upload Video
    </button>
</section>

<section class="upload-box" id="uploadBox"
         style="display:none">

    <h2>Upload Your Video</h2>

    <form id="uploadForm">

        <input
            type="text"
            id="videoTitle"
            placeholder="Enter video title"
            required
        >

        <input
            type="file"
            id="videoFile"
            accept="video/*"
            required
        >

        <button type="submit">
            Upload Video
        </button>

    </form>
</section>

<h2 class="section-title">
    🎮 VIDEO LIBRARY
</h2>

<section class="video-grid" id="videoGrid">

</section>

<footer>
    <p>© 2026 MR WISHWA</p>
    <p>Free Fire Gaming Videos</p>
</footer>

<script>
const uploadBox = document.getElementById("uploadBox");
const uploadForm = document.getElementById("uploadForm");
const videoGrid = document.getElementById("videoGrid");

let videos = [];

function showUpload() {
    uploadBox.style.display =
        uploadBox.style.display === "none"
        ? "block"
        : "none";
}

uploadForm.addEventListener("submit", function(event) {
    event.preventDefault();

    const title =
        document.getElementById("videoTitle").value.trim();

    const file =
        document.getElementById("videoFile").files[0];

    if (!file || !file.type.startsWith("video/")) {
        alert("Please select a video file.");
        return;
    }

    const video = {
        id: Date.now() + Math.random(),
        title: title,
        file: file,
        url: URL.createObjectURL(file)
    };

    videos.unshift(video);

    renderVideos();

    uploadForm.reset();
    uploadBox.style.display = "none";
});

function renderVideos() {
    videoGrid.innerHTML = "";

    videos.forEach(function(video) {
        const card = document.createElement("article");
        card.className = "video-card";

        const player = document.createElement("video");
        player.src = video.url;
        player.controls = true;
        player.preload = "metadata";

        const info = document.createElement("div");
        info.className = "video-info";

        const title = document.createElement("h3");
        title.textContent = video.title;

        const download = document.createElement("a");
        download.href = video.url;
        download.download = video.file.name;
        download.textContent = "⬇ Download";

        const remove = document.createElement("button");
        remove.className = "delete-btn";
        remove.textContent = "Delete";

        remove.addEventListener("click", function() {
            URL.revokeObjectURL(video.url);

            videos = videos.filter(function(item) {
                return item.id !== video.id;
            });

            renderVideos();
        });

        info.appendChild(title);
        info.appendChild(download);
        info.appendChild(remove);

        card.appendChild(player);
        card.appendChild(info);

        videoGrid.appendChild(card);
    });
}
</script>

</body>
</html>
