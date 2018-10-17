# hello-gradle-master
create spring boot 

### 少了bin file ，不知為何無法上船這些檔案，待釐清真相。
![image](https://user-images.githubusercontent.com/19975383/47081718-05af9b00-d23e-11e8-8dad-0518d6d30c65.png)
              

# Application.class.java

package lib;

import java.util.Arrays;

import org.springframework.boot.CommandLineRunner;

import org.springframework.boot.SpringApplication;

import org.springframework.boot.autoconfigure.SpringBootApplication;

import org.springframework.context.ApplicationContext;

import org.springframework.context.annotation.Bean;



@SpringBootApplication



public class Application {


    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
    @Bean
    public CommandLineRunner commandLineRunner(ApplicationContext ctx) {
        return args -> {
            System.out.println("Let's inspect the beans provided by Spring Boot:");
            String[] beanNames = ctx.getBeanDefinitionNames();
            Arrays.sort(beanNames);
            for (String beanName : beanNames) {
                System.out.println(beanName);
            }
        };
    }	
}



# Library.class

package lib;


import org.springframework.web.bind.annotation.RestController;

import java.util.Date;

import org.springframework.web.bind.annotation.RequestMapping;

import org.springframework.web.bind.annotation.ResponseBody;

@RestController



public class Library {

    @RequestMapping("/")
    
    public @ResponseBody String index() {
        return "user is tiro" + new Date();
    }
    public boolean someLibraryMethod() {
	// TODO 自動產生的方法 Stub
	return false;
	}
}



# LibraryTest.class

package lib;

import org.junit.Test;

import lib.Library;

import static org.junit.Assert.*;

public class LibraryTest {

    @Test public void testSomeLibraryMethod() {
        Library classUnderTest = new Library();
        assertTrue("someLibraryMethod should return 'true'", classUnderTest.someLibraryMethod());
    }
}
