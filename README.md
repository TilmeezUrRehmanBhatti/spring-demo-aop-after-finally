**Advice - Interaction**

<img src="https://user-images.githubusercontent.com/80107049/189758788-3b19c8a8-e3b7-4fda-a65e-8059259af319.png" width= 500 />


**Sequence Diagram**

<img src="https://user-images.githubusercontent.com/80107049/189758854-e86064ce-bb74-4cab-989b-0f97c2929877.png" width="500" />




+ @After will execute **before** @AfterThrowing

<img src="https://user-images.githubusercontent.com/80107049/189758914-3b482762-56eb-4809-8a97-bdc583f1adc8.png" width="500" />


**Use Cases**
+ Log the exception and/or perform auditing
+ Code to run regardless of method outcome
+ Encapsulate this functionality in AOP aspect for easy reuse


**Example**

+ Create an advice to after the method (finally ... success/failure)

```JAVA
@After("execution(* com.tilmeez.aopdemo.dao.AccountDAO.findAccounts(..))")
public void afterFinallyAccountsAdvice() {
  
  System.out.println("Executing @After (finally) advice");
  
}
```
+ The @After advice does not have access to the exception
  + If we need exception, then use @AfterThrowing advice

+ The @After advice should be able to run in the case of success or error
  + Code should not depend on happy path or an exception
  + Logging / auditing is the easiest case here

**Development Process - @After**
1. Pre work
2. Add @After advice
3. Test for failure/exception case
4. Test for success case

