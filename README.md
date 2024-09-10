html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Media Upload and Playback</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .upload-section, .playback-section {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <h1>Media Upload and Playback</h1>

    <div class="upload-section">
        <h2>Upload Media</h2>
        <input type="file" id="mediaUpload" accept="audio/*, video/*">
        <button id="uploadBtn">Upload</button>
        <p id="uploadStatus"></p>
    </div>

    <div class="playback-section">
        <h2>Play Media</h2>
        <video id="mediaPlayer" controls width="600" style="display:none;">
            Your browser does not support the video tag.
        </video>
        <audio id="audioPlayer" controls style="display:none;">
            Your browser does not support the audio tag.
        </audio>
    </div>

    <script>
        const uploadBtn = document.getElementById('uploadBtn');
        const mediaUpload = document.getElementById('mediaUpload');
        const mediaPlayer = document.getElementById('mediaPlayer');
        const audioPlayer = document.getElementById('audioPlayer');
        const uploadStatus = document.getElementById('uploadStatus');

        uploadBtn.addEventListener('click', () => {
            const file = mediaUpload.files[0];
            if (file) {
                const fileURL = URL.createObjectURL(file);
                if (file.type.startsWith('video/')) {
                    mediaPlayer.src = fileURL;
                    mediaPlayer.style.display = 'block';
                    audioPlayer.style.display = 'none';
                } else if (file.type.startsWith('audio/')) {
                    audioPlayer.src = fileURL;
                    audioPlayer.style.display = 'block';
                    mediaPlayer.style.display = 'none';
                }
                uploadStatus.textContent = 'Media uploaded successfully!';
            } else {
                uploadStatus.textContent = 'Please select a media file to upload.';
            }
        });
    </script>
</body>
</html>
