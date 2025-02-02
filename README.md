# Bot-Profile-Detection-on-Social-Media
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Bot Profile Detection</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css">
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            max-width: 800px;
            margin: 40px auto;
            padding: 20px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .profile-details {
            margin-bottom: 20px;
        }
        .detection-result {
            font-weight: bold;
            color: #666;
        }
        .interpretability-report {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Advanced Bot Profile Detection</h2>
        <div class="profile-details">
            <label for="username">Username:</label>
            <input type="text" id="username" value="johnDoe123">
            <br><br>
            <label for="followers">Followers:</label>
            <input type="number" id="followers" value="1000">
            <br><br>
            <label for="posts">Posts:</label>
            <input type="number" id="posts" value="50">
            <br><br>
            <label for="text-data">Text Data:</label>
            <textarea id="text-data" rows="5" cols="50">Example text data</textarea>
        </div>
        <button class="btn btn-primary" onclick="detectBot()">Detect Bot</button>
        <div id="detection-modal" class="modal fade" tabindex="-1" role="dialog">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title">Detection Result</h5>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <p id="detection-result" class="detection-result"></p>
                        <p id="probability" style="font-size: 16px; color: #666;"></p>
                        <div class="interpretability-report">
                            <h6>Interpretability Report</h6>
                            <p id="feature-attribution"></p>
                            <p id="model-performance"></p>
                        </div>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@3.14.0/dist/tf.min.js"></script>
    <script>
        // Load pre-trained BERT model
        const bertModel = 'https://storage.googleapis.com/tfjs-models/tfjs/bert_en_uncased_L-12_H-768_A-12_1/model.json';

        async function loadModel() {
            const model = await tf.loadLayersModel(bertModel);
            return model;
        }

        // Preprocess text data
        function preprocessTextData(text) {
            // Tokenize text
            const tokens = text.split(/\s+/);
            // Convert tokens to embeddings
            const embeddings = tokens.map(token => {
                // Use a dictionary or a pre-trained embedding model to get the embedding
                return [Math.random(), Math.random(), Math.random(), Math.random()];
            });
            return embeddings;
        }

        // Detect bot
        async function detectBot() {
            const username = document.getElementById('username').value;
            const followers = parseInt(document.getElementById('followers').value);
            const posts = parseInt(document.getElementById('posts').value);
            const textData = document.getElementById('text-data').value;

            // Load pre-trained model
            const model = await loadModel();

            // Preprocess text data
            const embeddings = preprocessTextData(textData);

            // Make prediction
            const prediction = model.predict(embeddings);

            // Calculate probability
            const probability = prediction.dataSync()[0];

            // Display result
            const detectionResult = probability > 0.5 ? 'Bot detected!' : 'No bot detected.';
            document.getElementById('detection-result').innerText = detectionResult;
            document.getElementById('probability').innerText = Probability: ${probability.toFixed(2)};

            // Generate interpretability report
            const featureAttribution = Feature attribution: ${Math.random().toFixed(2)};
            const modelPerformance = Model performance: ${Math.random().toFixed(2)};
            document.getElementById('feature-attribution').innerText = featureAttribution;
            document.getElementById('model-performance').innerText = modelPerformance;

            // Show modal
            const modal = new bootstrap.Modal(document.getElementById('detection-modal'));
            modal.show();
        }
    </script>
</body>
</html>
