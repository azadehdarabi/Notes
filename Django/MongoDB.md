
should create user in admin database

create admin  user:
`db.createUser({user: "admin", pwd: "admin", roles:[{role: "readWrite", db: "golmorad"}]})`

