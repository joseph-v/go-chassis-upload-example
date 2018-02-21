# go-chassis-upload-example

##How to run

- Get go-chassis 
```
mkdir -p /gopath/src/github.com/ServiceComb/
cd /gopath/src/github.com/ServiceComb/
git clone https://github.com/ServiceComb/go-chassis.git
```

- Download and run service-center (Refer https://github.com/apache/incubator-servicecomb-service-center)
```
wget https://github.com/apache/incubator-servicecomb-service-center/releases/download/0.5.0/service-center-0.5.0-linux-amd64.tar.gz
tar xf service-center-0.5.0-linux-amd64.tar.gz
cd service-center-0.5.0-linux-amd64
./start.sh
```

- Run example microservice
```
cd /gopath/src/github.com/joseph-v/go-chassis-upload-example
CHASSIS_CONF_DIR=/gopath/src/github.com/joseph-v/go-chassis-upload-example/conf go run main.go
```

- Testing example
```
echo "Test input" > /tmp/inputfile.txt
curl -X POST http://127.0.0.1:8083/uploadfile -H 'content-type: application/octet-stream' --data-binary '@/tmp/inputfile.txt'
cat uploaded-file.txt
echo "Test form" > input.txt
curl -X POST http://127.0.0.1:8083/uploadform -H 'content-type: multipart/form-data' -F uploadfile=@input.txt
cat uploaded-form.txt
```
