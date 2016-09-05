var student = [ 
         {"name": "Mette", "email": "mette@hotmail.com", "phone": "34343434", "category": "red", "group name": ""}, 
         {"name": "Jens", "email": "jens@hotmail.com", "phone": "43434343", "category": "yellow", "group name": ""},
         {"name": "Poul", "email": "poul@hotmail.com", "phone": "57575757", "category": "green", "group name": ""},
         {"name": "Anne", "email": "anne@hotmail.com", "phone": "75757575", "category": "green", "group name": ""},
         {"name": "Mimmi", "email": "mimmi@hotmail.com", "phone": "89898989", "category": "yellow", "group name": ""},
         {"name": "Signe", "email": "signe@hotmail.com" , "phone": "98989898", "category": "green", "group name": ""},
         {"name": "Mads", "email": "mads@hotmail.com", "phone": "24541222", "category": "green", "group name": ""}
     ]; 
     var addStudent = function (name, email, phone, category, groupname) { 
         var student = {}; 
         student.name = name; 
         student.email = email; 
         student.phone = phone; 
         student.category = category;
         student.groupname = groupname;
         student.push(student); 
     }; 
     
     var student = document.getElementById("addStudent"); 
     student.onclick = function (event) {                 
         event.preventDefault(); 
         var form = document.getElementById("inputform"); 
         var textA = document.createElement("TEXTAREA"); 
         textA.setAttribute("placeholder","enter one student pr text field"); 
         textA.setAttribute("class",""); 
         form.insertBefore(textA, form.childNodes[form.childNodes.length-2]); 
         return false; 
     }; 
 
     var populateTable = function () { 
         var tbody = document.getElementById("list"); 
         var rowCountPlus = tbody.rows.length + 1; 
         if (rowCountPlus > 1) 
             while (--rowCountPlus) 
                 tbody.deleteRow(rowCountPlus - 1); 
         for (var i = 0; i < student.length; i++) { 
             var row = tbody.insertRow(i); 
             row.insertCell(0).innerHTML = student[i].name; 
             row.insertCell(1).innerHTML = student[i].email; 
             row.insertCell(2).innerHTML = student[i].phone; 
             row.insertCell(2).innerHTML = student[i].category; 
             row.insertCell(2).innerHTML = student[i].groupname; 
         } 
     }; 
     populateTable(); 
     var emptyFormFields = function(form){ 
         var inputs = form.getElementsByTagName("input"); 
         for (var i = 0; i < inputs.length; i++) { 
             if(inputs[i].getAttribute("type")!== "submit") 
             inputs[i].value = ""; 
         } 
     }; 
     var form = document.getElementById("inputform"); 
     form.submit = function (event) { 
         event.preventDefault(); 
         var student = { 
             "name": form.elements["firstname"].value, 
             "email": form.elements["email"].value, 
             "phone": form.elements["phone"].value,
             "category": form.elements["phone"].value, 
             "groupname": form.elements["phone"].value 
         }; 
         addStudent(student.name, student.email, student.phone, student.category, student.groupname); 
         populateTable(); 
         emptyFormFields(this); 
         return false; 
     }; 
 
 



