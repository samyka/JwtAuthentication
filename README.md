For more detail, please visit:

# Secure Spring Boot App with Spring Security & JWT Authentication

## Run Spring Boot application
```
mvn spring-boot:run
```

#Authentication. You’ll know:

- Appropriate Flow for User Signup & User Login with JWT Authentication
- Spring Boot Application Architecture with Spring Security
- How to configure Spring Security to work with JWT
- How to define Data Models and association for Authentication and Authorization
- Way to use Spring Data JPA to interact with PostgreSQL/MySQL Database
- Lots of interesting things ahead, let’s explore together. 

#For MySQL

- spring.datasource.url= jdbc:mysql://localhost:3306/testdb?useSSL=false
- spring.datasource.username= root
- spring.datasource.password= 123456

- spring.jpa.properties.hibernate.dialect= org.hibernate.dialect.MySQL5InnoDBDialect
- spring.jpa.hibernate.ddl-auto= update

#For PostgreSQL

- spring.datasource.url= jdbc:postgresql://localhost:5432/testdb
- spring.datasource.username= postgres
- spring.datasource.password= 123

- spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation= true
- spring.jpa.properties.hibernate.dialect= org.hibernate.dialect.PostgreSQLDialect

# Hibernate ddl auto (create, create-drop, validate, update)
spring.jpa.hibernate.ddl-auto= update


## Run following SQL insert statements
```
INSERT INTO roles(name) VALUES('ROLE_USER');
INSERT INTO roles(name) VALUES('ROLE_MODERATOR');
INSERT INTO roles(name) VALUES('ROLE_ADMIN');
```

##Controller for testing Authorization
```
There are 4 APIs:
– /api/test/all for public access
– /api/test/user for users has ROLE_USER or ROLE_MODERATOR or ROLE_ADMIN
– /api/test/mod for users has ROLE_MODERATOR
– /api/test/admin for users has ROLE_ADMIN
```
```
Register some users with /signup API:
admin with ROLE_ADMIN
mod with ROLE_MODERATOR and ROLE_USER
zkoder with ROLE_USER
```

##Create Spring RestAPIs Controllers

```
Controller for Authentication

This controller provides APIs for register and login actions.

– /api/auth/signup

check existing username/email
create new User (with ROLE_USER if not specifying role)
save User to database using UserRepository
– /api/auth/signin

authenticate { username, pasword }
update SecurityContext using Authentication object
generate JWT
get UserDetails from Authentication object
response contains JWT and UserDetails data
```
# JwtAuthentication
