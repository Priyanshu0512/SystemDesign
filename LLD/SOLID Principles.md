SOLID is a set of five principles for designing object-oriented software that is easier to change, test, and maintain.

> [!Full Form]
> S    - Single responsibility Principle (SRP)
> O    -  Open Closed Principle (OCP)
> L    -   Liskov substitution Principle (LSP)
> I     -  Interface segregation Principle (ISP)
> D    - Dependency Inversion Principle (DSP)

## Single responsibility Principle(SRP)

#### Problematic Code 
```java

class Employee{  
  
    private String name;  
    private String address;  
    private int id;  
  
    Employee(int id, String name,String address ){  
        this.id=id;  
        this.name=name;  
        this.address=address;  
    }  
    public double computeSalary(){  
        System.out.println("Computed Salary");  
        return 10000.0;  
    }  
    public void printEmployeePerformance(){  
        System.out.println("Performance data");  
    }  
    public void fetchEmployeeData(){  
        System.out.println("Employee Data"+name);  
    }
}

```

The above class has too many reasons to change in future as it it trying to handle multiple methods which might need modification in the future.This violates the SRP.

**Single Responsibility Principle states that the class should have only one and one reason to change.** Every class should handle one core logic which can change in future.

> A "monster class" (also known as a God Class or Blob) is an anti-pattern that directly violates the Single Responsibility Principle (SRP)—the very first rule of SOLID.

A better implementation of the above code snippet will be to segregate the three methods into their own classes hence giving then a single responsibility to cater to.

> [!note]
> If a method inside a class is itself is a containing a large piece of code leveraging other methods of the same class and is  algorithmically bulky then it can be also moved in a separate class file of its own. (Though this is opinionated.)

---

## Open/Closed Responsibility Principle(OCP)

Problematic Code 

```java
// Notification sender
import java.util.List;
public class NotificationSender {
	public void sendotifications(List<NotificationType> notificationTypes, String message) (
	for (NotificationType notificationType : notificationTypes) {
		switch (notificationType) {
			case SMS:
				notificationType. sendSMSNotification(message);
				break;
			case EMAIL:
				notificationType.sendEmailNotification(message);
				break;
			case PUSH:
				notificationType.sendPushNotification(message);
				break;
			case WHATSAPP:
				notificationType.sendwhatsAppNotification(message);
				break:
		}
	}
}


// Notification Type seperate file 
public enum NotificationType {
	SMS,
	EMAIL,
	PUSH,
	WHATSAPP;
	public void sendSMSNotification (String message) {
		System. out.printIn("SMS: " + message);
	}
	public void sendEmailNotification(String message) {
		System.out.println("Email: " + message);
	}
	public void sendPushNotification(String message) {
		System.out•println("Push: " + message);
	}
	public void sendwhatsAppNotification(String message) {
		System.out-printIn("WhatsApp: " + message);
}
```

The above code snippet is 
