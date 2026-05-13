# Anypoint Platform Development: Production-Ready Development Practices - DEX660

## Local Path
- PROJECT_HOME=/Users/yehan.jeong/Desktop/dex660-202605
- STUDENT_FILE=/Users/yehan.jeong/Desktop/DEX660-WI25v1-EN-Student-Files

## Anypoint Platform Information
- Mule Account: yehan202605

### Business Group
- Business Group ID: 477c325e-4f61-4844-8743-4969798259c4
- Client ID: 16c09c01413547018d8acef6738e5ca8
- Client Secret: 1f63a29B32704a968a6aB7c97A61C89b

### Connected App 
- Exchange Contributor ID: 
- Exchange Contributor Secret: 
- CloudHub Deployment ID: 
- CloudHub Deployment Secret: 

### API Instance ID:
- prod: 20904505
- test:
- dev:

## Commands
- export PROJECT_HOME=/Users/yehan.jeong/Desktop/dex660-202605
- export STUDENT_FILE=/Users/yehan.jeong/Desktop/DEX660-WI25v1-EN-Student-Files
- echo $PROJECT_HOME
- echo $STUDENT_FILE
- cd $PROJECT_HOME/check-in-papi/src/main/resources
- PASS="mule12345"
APP="check-in-papi"
HOSTNAME="localhost"
ALTNAMES="DNS:$HOSTNAME,IP:127.0.0.1"
KEYSTORE="$APP.p12"
DNAME="cn=$HOSTNAME, ou=Training, o=MuleSoft, c=US"
- keytool -v -genkeypair -keyalg RSA -dname "$DNAME" \
-ext SAN="$ALTNAMES" -validity 365 -alias server \
-keystore "$KEYSTORE" -storetype pkcs12 -storepass "$PASS"
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\":\"Smith\",\"numBags\":2}" https://localhost:8081/api/v1/tickets/PNR123/checkin
- -M-Danypoint.platform.client_id=16c09c01413547018d8acef6738e5ca8 -M-Danypoint.platform.client_secret=1f63a29B32704a968a6aB7c97A61C89b
