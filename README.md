# camera-test
[camera-test.html](https://github.com/user-attachments/files/27315515/camera-test.html)
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로컬 카메라 테스트</title>
    <style>
        body { font-family: Arial; text-align: center; margin: 20px; }
        video { width: 640px; max-width: 100%; border: 2px solid #333; border-radius: 8px; }
        button { padding: 12px 24px; font-size: 18px; margin: 10px; }
    </style>
</head>
<body>
    <h1>로컬 카메라 테스트</h1>
    <p>버튼을 누르면 카메라 권한을 요청합니다.</p>
    
    <button onclick="startCamera()">📹 카메라 켜기</button>
    <button onclick="stopCamera()">⏹️ 카메라 끄기</button>
    
    <br><br>
    <video id="video" autoplay playsinline></video>
    
    <script>
        let stream = null;

        async function startCamera() {
            try {
                // 카메라만 요청 (마이크는 false)
                stream = await navigator.mediaDevices.getUserMedia({ 
                    video: true, 
                    audio: false 
                });
                
                const video = document.getElementById('video');
                video.srcObject = stream;
                console.log("✅ 카메라가 켜졌습니다.");
            } catch (err) {
                console.error("❌ 오류:", err);
                alert("카메라 접근이 거부되었거나 오류가 발생했습니다.\n" + err.message);
            }
        }

        function stopCamera() {
            if (stream) {
                stream.getTracks().forEach(track => track.stop());
                document.getElementById('video').srcObject = null;
                stream = null;
                console.log("⏹️ 카메라가 꺼졌습니다.");
            }
        }

        // 페이지 종료 시 자동 정리
        window.addEventListener('beforeunload', stopCamera);
    </script>
</body>
</html>
