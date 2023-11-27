# Details  
This this my  API testing project. This repository contains a Postman collection and environment designed to facilitate API testing for various functionalities related to student management. The API allows operations such as fetching student details, creating new students, retrieving specific students, adding technical skills, and managing student addresses. 
About student details, Create Student, Get Specific Student, Create Technical Skills, and Create Student Address.
 Here in this API student details viewed and different tests were performed like GET, POST, PUT, DELETE.
<p align="center">
                                                                                                                                                                                                                                            
 Test Scripts 6 and Total 20 assertions were done. All of them passed with 0 skipped tests. The number of iteration was 1.

 < />
# Assertions Details    
#### Get Student
**Test Script**
```bash
var jsonData = pm.response.json()
var ststuscode = pm.response.code
console.log(jsonData.length)

if(ststuscode==200){
var jsonData = pm.response.json()
pm.test(" 200 OK", function(){
    pm.response.to.have.status(200);
});
}
else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}

else if(ststuscode==201){

    pm.test("Created", function(){
    pm.response.to.have.status(201);
    });
}

else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}     
```
#### Create Student
**Body**
```bash   
{
"first_name": "{{firstName}}", 
"middle_name": "{{middleName}}", 
"last_name": "{{lastName}}", 
"date_of_birth": "{{date_of_birth}}" 
}
```

**Pre-Request Scripts**

```bash   
var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
console.log("First Name Value:  "+ firstName)
pm.environment.set("firstName",firstName)

var middleName = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Middle Name Value:  "+ middleName)
pm.environment.set("middleName",middleName)

var lastName = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Last Name Value:  "+ lastName)
pm.environment.set("lastName",lastName)

const moment = require('moment')
const today = moment()
console.log(today.format("YYYY-MM-DD"))
pm.environment.set("date_of_birth",today.add(1,'d').format("YYYY-MM-DD"))
```
**Test Script**
```bash
var jsonData = pm.response.json()
pm.environment.set("id", jsonData.id)

var ststuscode = pm.response.code
console.log(ststuscode)

if(ststuscode==201){
var jsonData = pm.response.json()
pm.test(" 201 Created", function(){
    pm.response.to.have.status(201);
});
}
else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}



else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}
});
```   
#### Get Specific Student  
**Test Script**
```bash
var ststuscode = pm.response.code
console.log(ststuscode)

if(ststuscode==200){
var jsonData = pm.response.json()
pm.test("Status code is 200", function(){
    pm.response.to.have.status(200);
});

pm.test("ID Validate", function(){
    pm.expect(jsonData.data.id).to.eql(pm.environment.get("id"));

});

pm.test("First Name Validate", function(){
    pm.expect(jsonData.data.first_name).to.eql(pm.environment.get("firstName"));

});

pm.test("Middle Name Validate", function(){
    pm.expect(jsonData.data.middle_name).to.eql(pm.environment.get("middleName"));

});

pm.test("Last Name Validate", function(){
    pm.expect(jsonData.data.last_name).to.eql(pm.environment.get("lastName"));

});

pm.test("Date of Birth Validate", function(){
    pm.expect(jsonData.data.date_of_birth).to.eql(pm.environment.get("date_of_birth"));

});

}

else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}

else if(ststuscode==201){

    pm.test("Created", function(){
    pm.response.to.have.status(201);
    });
}

else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}

```   
#### Create Technical Skills
**Body**
```bash
{ 
"id": 1, 
"language": [ 
"sample string 1", 
"sample string 2" 
], 
"yearexp": "sample string 2", 
"lastused": "sample string 3", 
"st_id": {{id}}
}
```
**Test Script**
```bash
var ststuscode = pm.response.code
console.log(ststuscode)

if(ststuscode==200){
var jsonData = pm.response.json()
pm.test(" 200 OK", function(){
    pm.response.to.have.status(200);
});
}
else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}

else if(ststuscode==201){

    pm.test("Created", function(){
    pm.response.to.have.status(201);
    });
}

else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}
```

#### Create Student Address 
**Body**
```bash
{ 
"Permanent_Address": { 
"House_Number": "sample string 1",
"City": "sample string 2",
 "State": "sample string 3", 
"Country": "sample string 4",
"PhoneNumber": [ 
{ 
"Std_Code": "sample string 1",
"Home": "sample string 2",
 "Mobile": "sample string 3" 
},
{ 
"Std_Code": "sample string 1",
"Home": "sample string 2", 
"Mobile": "sample string 3" 
} 
] 
},
"stId": {{id}}
}

```
**Test Script**
```bash


var ststuscode = pm.response.code
console.log(ststuscode)

if(ststuscode==200){
var jsonData = pm.response.json()
pm.test(" 200 OK", function(){
    pm.response.to.have.status(200);
});

pm.test("Status Validate", function(){
    pm.expect(jsonData.status).to.eql("true");

});

pm.test("Massage Validate", function(){
    pm.expect(jsonData.msg).to.eql("Add  data success");

});

}
else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}

else if(ststuscode==201){

    pm.test("Created", function(){
    pm.response.to.have.status(201);
    });
}

else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}

```  

#### Final Student Details 
**Test Script**
```bash


var ststuscode = pm.response.code
console.log(ststuscode)

if(ststuscode==200){
var jsonData = pm.response.json()
pm.test(" 200 OK", function(){
    pm.response.to.have.status(200);
});

pm.test("Language Field Validation", function () {
    pm.expect(pm.response.json().data.TechnicalDetails[0].language).to.be.an('array').that.includes.members(["sample string 1", "sample string 2"]);
});


pm.test("Year of Experience (yearexp) Validation", function () {
    pm.expect(pm.response.json().data.TechnicalDetails[0].yearexp).to.be.a('string');
});

pm.test("House Number Validation", function () {
    pm.expect(pm.response.json().data.Address[0].Permanent_Address.House_Number).to.be.a('string');
});

pm.test("City Validation", function () {
    pm.expect(pm.response.json().data.Address[0].Permanent_Address.City).to.be.a('string');
});

pm.test("Country Validation", function () {
    pm.expect(pm.response.json().data.Address[0].Permanent_Address.Country).to.be.a('string');
});

pm.test("Mobile Numbers Validation", function () {
    const mobileNumbers = pm.response.json().data.Address[0].Permanent_Address.PhoneNumber;
    pm.expect(mobileNumbers).to.be.an('array');
    mobileNumbers.forEach((number) => {
        pm.expect(number.Mobile).to.be.a('string');
    });
});


pm.test("Current Address Validation", function () {
    pm.expect(pm.response.json().data.Address[0].Current_Address).to.be.null;
});



}
else if(ststuscode==404){

    pm.test("Not Found", function(){
    pm.response.to.have.status(404);
    });
}

else if(ststuscode==200){

    pm.test("OK", function(){
    pm.response.to.have.status(200);
    });
}

else if(ststuscode==201){

    pm.test("Created", function(){
    pm.response.to.have.status(201);
    });
}

else if(ststuscode==202){

    pm.test("Accepted", function(){
    pm.response.to.have.status(202);
    });
}

else if(ststuscode==400){

    pm.test("Bad Request", function(){
    pm.response.to.have.status(400);
    });
}

else if(ststuscode==401){

    pm.test("Unauthorized", function(){
    pm.response.to.have.status(401);
    });
}

else if(ststuscode==403){

    pm.test("Fordidden", function(){
    pm.response.to.have.status(403);
    });
}

else if(ststuscode==405){

    pm.test("Method Not Allowed", function(){
    pm.response.to.have.status(405);
    });
}

else if(ststuscode==500){

    pm.test("Internal Server Error", function(){
    pm.response.to.have.status(500);
    });
}

else if(ststuscode==501){

    pm.test("Not Implimented", function(){
    pm.response.to.have.status(501);
    });
}

else if(ststuscode==502){

    pm.test("Bad Gateway", function(){
    pm.response.to.have.status(502);
    });
}

else if(ststuscode==503){

    pm.test("Service Unavailable", function(){
    pm.response.to.have.status(503);
    });
}

else{
    pm.test("Something Else!!!!")
}
```   



