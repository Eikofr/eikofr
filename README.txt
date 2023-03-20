<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSV File Upload</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        form {
            max-width: 400px;
            margin: 20px auto;
        }

        input[type="submit"] {
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>CSV File Upload</h1>
    <form id="upload-form" enctype="multipart/form-data">
        <label for="csv-file">Select a CSV file:</label>
        <input type="file" id="csv-file" name="csv-file" accept=".csv" required>
        <br>
        <input type="submit" value="Upload CSV">
    </form>
    <script>
        document.getElementById('upload-form').addEventListener('submit', async (event) => {
            event.preventDefault();

            const fileInput = document.getElementById('csv-file');
            const formData = new FormData();
            formData.append('csv-file', fileInput.files[0]);

            try {
                const response = await fetch('/upload', {
                    method: 'POST',
                    body: formData,
                });

                if (response.ok) {
                    alert('CSV file uploaded successfully.');
                } else {
                    alert('Error uploading CSV file.');
                }
            } catch (error) {
                console.error('Error:', error);
                alert('Error uploading CSV file.');
            }
        });
    </script>
</body>
</html>
