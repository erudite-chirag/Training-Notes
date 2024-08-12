**Table of contents**
- [[#Agenda:|Agenda:]]
	- [[#Agenda:#Relational Mapping|Relational Mapping]]
		- [[#Relational Mapping#One-to-One Relationships|One-to-One Relationships]]
		- [[#Relational Mapping#One-to-Many Relationships|One-to-Many Relationships]]
		- [[#Relational Mapping#Many-to-Many Relationships|Many-to-Many Relationships]]
	- [[#Agenda:#CommandLineRunner|CommandLineRunner]]
	- [[#Agenda:#run Method|run Method]]


## Agenda:
- Relational Mapping - 
	- One to One Relationships
	- One to Many Relationships
	- Many to Many Relationships (theory)
	        

### Relational Mapping

#### One-to-One Relationships

**What is a One-to-One Relationship?** 
A one-to-one relationship is a type of association between two entities where each instance of one entity is associated with one instance of another entity.

**Example:** Consider a `User` and `Profile`. Each user has one profile, and each profile belongs to one user.

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;

    @OneToOne(mappedBy = "user")
    private Profile profile;
    // Getters and setters
}

@Entity
public class Profile {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String bio;

    @OneToOne
    @JoinColumn(name = "user_id")
    private User user;
    // Getters and setters
}
```


#### One-to-Many Relationships

**What is a One-to-Many Relationship?** 
A one-to-many relationship is where one entity is associated with multiple instances of another entity.

**Example:** Consider a `User` and `Post`. Each user can have multiple posts, but each post belongs to one user.

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;

    @OneToMany(mappedBy = "user")
    private List<Post> posts;
    // Getters and setters
}

@Entity
public class Post {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String content;

    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;
    // Getters and setters
}
```

#### Many-to-Many Relationships

**What is a Many-to-Many Relationship?** 
A many-to-many relationship is where multiple instances of one entity are associated with multiple instances of another entity.

**Example:** Consider `Electronics` and `Mobile Phones`.


### CommandLineRunner

`CommandLineRunner` is an interface provided by Spring Boot. It has a single method, `run`, which is called just before the application context is refreshed and after all Spring Beans are initialized. This makes it a useful interface for executing code that you want to run once the application starts. Typically, it's used for initializing data, running some setup routines, or performing tasks that need to happen at application startup.

### run Method

The `run` method is the single abstract method defined by the `CommandLineRunner` interface. It is implemented to perform the actions you want to execute when the application starts.
