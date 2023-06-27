
should create user in admin database
db.createUser({user: "admin", pwd: "admin", roles:[{role: "readWrite", db: "golmorad"}]})

