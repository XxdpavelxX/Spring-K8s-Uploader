## Docker deployment

Stored in dockerfile

### Build the app in a docker image
docker build -t celonis-app:1.0.0 .

### Run the app on a docker container
docker run -p 8080:8080 celonis-app
(add "-d" flag to run in the background)

### Upload a file
curl -X POST http://localhost:8080/files -H 'Celonis-Auth: dev' -F file=@\path_to_file\upload_test.jpg

# curl.exe -X POST http://localhost:8080/files -H 'Celonis-Auth: dev' -F file=@\Users\dpave\Downloads\challenge_Pavel\challenge_Pavel\upload_test.jpg
Note: Use curl.exe for Windows powershell


### Download file
curl -LO http://localhost:8080/files/upload_test.jpg
