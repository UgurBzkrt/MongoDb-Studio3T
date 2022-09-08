# MongoDB

$ apt update -y

- for key:

$ sudo apt install gnupg

- MongoDB public GPG Key:

$ sudo apt install wget curl gnupg2 software-properties-common apt-transport-https ca-certificates lsb-release

$ curl -fsSL https://www.mongodb.org/static/pgp/server-6.0.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/mongodb-6.gpg

$ echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

$ (18.04) echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

$ sudo apt update

$ sudo apt install mongodb-org

$ sudo systemctl enable --now mongod


---------------

- 22.04:

$ apt update -y

$ curl -fsSL https://www.mongodb.org/static/pgp/server-6.0.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/mongodb-6.gpg

$ echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

$ wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb

$ sudo dpkg -i ./libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb

$ sudo apt update

$ sudo apt install mongodb-org

$ sudo systemctl enable --now mongod

# Enable Password Authentication on MongoDB 6.0

$ security:
  authorization: enabled
  
# Remote Access:

$ net:
  port: 27017
  bindIp: 127.0.0.1  # Enter 0.0.0.0,:: to bind to all IPv4 and IPv6 addresses or, alternatively, use the net.bindIpAll setting.
  
$ sudo systemctl restart mongod

$ sudo ufw allow 27017

# MongoDB shell:

$ mongosh

# Create a User and Add a Role in MongoDB:

use admin
db.createUser(
{
user: "mongdbuser",
pwd: passwordPrompt(), // or cleartext password
roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
}
)

# Check for user:

$ mongosh -u mongdbuser -p --authenticationDatabase admin

> show dbs

# Create and access empty db:

> use mongotestdb

sudo systemctl enable --now mongod


mongosh "mongodb://localhost:27017" > connect

$ mongosh >>  test> use admin

# create user and attach role:

db.createUser(
{ 
 user: "hello_admin",
 pwd:  "hello123",
 roles:
 [
 { role:"readWrite",db:"admin"},
 "clusterAdmin"
 ] } );
 
$ mongosh -u mongdbuser -p --authenticationDatabase admin

# CreateDB:
$ > use mongotestdb  < yoksa olusturmus olur.

# Collection create:

db.employeedetails.insertOne(
   {F_Name: "John",
    L_NAME: "Doe",
    ID_NO: "23245",
     AGE: "25",
     TEL: "63365467666"
   }
)
# Authentication user:
# Burada admin veritabanında “restrict” isimli bir kullanıcı oluşturuyoruz. Dolayısıyla bu kullanıcı, yalnızca 192.168.65.10 IP adresinden bu sunucu adresi IP adresi 198.157.56.0'a bağlanıyorsa kimlik doğrulaması yapabilir.

use admin
db.createUser(
   {
     user: "restrict",
     pwd: passwordPrompt(),
     roles: [ { role: "readWrite", db: "example" } ],
     authenticationRestrictions: [ {
        clientSource: ["192.168.65.10"],
        serverAddress: ["198.157.56.0"]
     } ]
   }
)

# ip
ip addr
$ curl ifconfig.me > 78.174.3.189

# Studio T3:

localhost:27017

mongodb://{username}:{password}@{ip_address}:{port}/?authSource=admin



