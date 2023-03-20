<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <title>CSV File Upload</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }

        .card {
            max-width: 400px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .card-footer {
            background-color: #f0f0f0;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="card-header">CSV File Upload</div>
        <div class="card-body">
            <form id="upload-form" enctype="multipart/form-data">
                <div class="mb-3">
                    <label for="csv-file" class="form-label">Select a CSV file:</label>
                    <input class="form-control" type="file" id="csv-file" name="csv-file" accept=".csv" required>
                </div>
                <button type="submit" class="btn btn-success">Upload CSV</button>
            </form>
        </div>
        <div class="card-footer">Made with ❤️ by YourName</div>
    </div>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha384-KyZXEAg3QhqLMpG8r+Knujsl5/9enJ0cz7IvyKnIDzyo2IKRV2ZrStlPS7A+EB5J" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
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
