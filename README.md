# Swagger_UI
Automation of Swagger_UI using frameworks such as--java,maven,TestNG,Rest-Assured_API-,JSON
package maven_Test_Package;

import java.util.HashMap;

import org.testng.annotations.Test;

import io.restassured.RestAssured;
import io.restassured.path.json.JsonPath;
import io.restassured.response.Response;

import static io.restassured.RestAssured.*;

class DemoGet {

	@Test(priority=1)
	public void sendGetRequest() {
		RestAssured.baseURI="https://reqres.in/";
		RestAssured.basePath="api/users/,";
		Response response=RestAssured.given()

				.when()
				//  .get("https://reqres.in/api/users/")
				.get()


				.then()

				.extract().response();

		String body= response.getBody().asString();
		System.out.println("Body of get API is " +body);
		int statusCode= response.getStatusCode();
		System.out.println("The status code is "+statusCode);

		JsonPath json= response.jsonPath();
	} 


	@Test(priority=2)
		public void PostLogin(){
			HashMap inputs=new HashMap();
			
				 inputs.put("username", "george.bluth@reqres.in"); 
				 inputs.put("email", "george.bluth@reqres.in");
				 inputs.put("password", "george");
				
				 Response response=
				 given()
				 .contentType("application/json")
				 .body(inputs)
				 .when()
				 .post("https://reqres.in/api/login")
				 .then()
				.statusCode(200)
				.log().body().extract().response();
				 
				 String body=response.getBody().asString();
			       System.out.println("Body of the code is "+body);
			
		}
		@Test(priority=3)
		public void  sendPostRegister(){
			HashMap inputs=new HashMap();
			
			// data.put("username", "emma.wong@reqres.in"); 
			inputs.put("email", "eve.holt@reqres.in");
			inputs.put("password", "Hakunamatata");
			 Response response=RestAssured.given()
					 .body(inputs)
				        .when().post("https://reqres.in/api/register")
				        .then()
				        .extract().response();
				        
				       String body=response.getBody().asString();
				       System.out.println("Body of the code is "+body);
				       
				       int statusCode=response.getStatusCode();
				       System.out.println("Status code is "+statusCode);
				       }
		
		@Test
		public void putUserId(){
			HashMap inputs=new HashMap();
			
			inputs.put("id", 20); 
			 Response response=RestAssured.given()
					 .body(inputs)
				        .when().put("https://reqres.in/api/users/2")
				        .then()
				 .statusCode(200)
				        .log().body()
				        .extract().response();
				        
			
			
		}
		@Test
		public  void deleteUserId() {
			HashMap inputs=new HashMap();
			
			 Response response=RestAssured.given()
					 .body(inputs)
				        .when().delete("https://reqres.in/api/users/2")
				        .then()
				 .statusCode(204)
				        .log().body()
				        .extract().response();
			 String body= response.getBody().asString();
			 System.out.println("The body is"+body);
				        
		}
		
			
	}



				
				
