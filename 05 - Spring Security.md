


## Agenda
- Authentication and Authorisation
- Introduction to Spring Security
- Role-based access control
	- Using the Security Configuration file
	- Using @PreAuth annotation



### Authentication: 
Process of verifying user credentials.
### Authorisation: 
Process of determining what authenticated users are allowed to do.
### Introduction to Spring Security: 
Spring Security is a powerful and highly customisable authentication and access control framework. It provides comprehensive security services for Java EE-based enterprise software applications.

### Hands-On 

1. Go to Spring Initialiser - and download SpringSecurity Project with the following dependencies:
	1. Spring Web
	2. Lombok
	3. Spring Security
2. Open the Project and Run it 
	1. Try to log in using the username as 'user' and password from the logs.
3. Go to application.properties and set Custom username and password
```properties
spring.security.user.name=Testing 
spring.security.user.password=test123
```
4. Create `AccessController` in the controllers directory
```java
@RestController  
@RequestMapping("/")  
public class AccessConrtoller {  
  
    @GetMapping  
    public String homePage(){  
        return "WELCOME TO SPRING SECURITY HOME PAGE";  
    }  
  
    @GetMapping("subscriber")  
    public String paidContent(){  
        return "THIS CONTENT IS FOR OUR PAID USERS ONLY.";  
    }  
  
    @GetMapping("admin")  
    public String adminDashboard(){  
        return "WELCOME ADMIN! HERE ARE YOU SETTINGS.";  
    }  

    @GetMapping("maintain")  
    public String maintainPage(){  
        return "MAINTENANCE HAPPENING HERE!";  
    }  
}
```
5. 

