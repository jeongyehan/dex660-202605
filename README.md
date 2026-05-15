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
- Exchange Contributor ID: 54c95379c7e44b529e6434d85c4465a5
- Exchange Contributor Secret: baEfF511D9FC47bcbF8D68f3D7Dd0ccC
- CloudHub Deployment ID: 0618ee2c71844ef5936eeb6b54277e07
- CloudHub Deployment Secret: B307fEC1960847cc9E831da17fFD61Fe

### API Instance ID:
- prod: 20904505
- test:20907425
- dev: 20907417

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
- cd $PROJECT_HOME
- cp -R check-in-papi check-in-papi-template
- cd $PROJECT_HOME 
- mkdir parent-pom
- cp $STUDENT_FILE/solutions/walkthroughs/devprd/module02/wt2-2_solution/parent-pom/pom.xml parent-pom/pom.xml
- mkdir bom
- cp $STUDENT_FILE/solutions/walkthroughs/devprd/module02/wt2-2_solution/bom/pom.xml bom/pom.xml
- cd $PROJECT_HOME/check-in-papi
- mvn clean verify
- cd $PROJECT_HOME/check-in-papi
- mvn clean deploy
- mvn clean deploy -DmuleDeploy -Dap.client_id=16c09c01413547018d8acef6738e5ca8 -Dap.client_secret=1f63a29B32704a968a6aB7c97A61C89b -Dap.ca.client_id=0618ee2c71844ef5936eeb6b54277e07 -Dap.ca.client_secret=B307fEC1960847cc9E831da17fFD61Fe
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\":\"Smith\",\"numBags\":2}" https://check-in-papi-oj3ymg.5sc6y6-4.usa-e2.cloudhub.io/api/v1/tickets/PNR123/checkin
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\":\"Smith\",\"numBags\":2}" https://localhost:8081/api/v1/tickets/PNR123/checkin
- -M-Denv=test
- -M-Denv=prod
- -M-Dencrypt.key=secure12345
- cd $PROJECT_HOME/check-in-papi
- mvn clean deploy -Dencrypt.key=secure12345
- mvn clean deploy -DmuleDeploy -Dap.client_id=16c09c01413547018d8acef6738e5ca8 -Dap.client_secret=1f63a29B32704a968a6aB7c97A61C89b -Dap.ca.client_id=0618ee2c71844ef5936eeb6b54277e07 -Dap.ca.client_secret=B307fEC1960847cc9E831da17fFD61Fe -Dencrypt.key=secure12345 -Ddeployment.env=dev
- mvn clean deploy -DmuleDeploy -Dap.client_id=16c09c01413547018d8acef6738e5ca8 -Dap.client_secret=1f63a29B32704a968a6aB7c97A61C89b -Dap.ca.client_id=0618ee2c71844ef5936eeb6b54277e07 -Dap.ca.client_secret=B307fEC1960847cc9E831da17fFD61Fe -Dencrypt.key=secure12345 -Ddeployment.env=test
- mvn clean deploy -DmuleDeploy -Dap.client_id=16c09c01413547018d8acef6738e5ca8 -Dap.client_secret=1f63a29B32704a968a6aB7c97A61C89b -Dap.ca.client_id=0618ee2c71844ef5936eeb6b54277e07 -Dap.ca.client_secret=B307fEC1960847cc9E831da17fFD61Fe -Dencrypt.key=secure12345 -Ddeployment.env=prod -Ddeployment.suffix=
- curl -ik https://localhost:8081/alive
- curl -ik https://localhost:8081/ready
- cd $PROJECT_HOME/check-in-papi
- mvn clean deploy -Dencrypt.key=secure12345
- mvn clean deploy -DmuleDeploy -Dap.client_id=16c09c01413547018d8acef6738e5ca8 -Dap.client_secret=1f63a29B32704a968a6aB7c97A61C89b -Dap.ca.client_id=0618ee2c71844ef5936eeb6b54277e07 -Dap.ca.client_secret=B307fEC1960847cc9E831da17fFD61Fe -Dencrypt.key=secure12345 -Ddeployment.env=dev
