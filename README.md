# python-group-project
**Humber College Admission Department Project**

In a group of 4, we utilized Python to generate reports indicating the newly admitted students and assign them to schools according to their GPA.

#1. **Welcoming message to the user**


```python
def welcome_message():
  print("Welcome to Humber College!")
```

#2. **Define functions to allow the user to log in using a PW which satisfy the ff: Rules:/ Should Contain atleast one upper case letter**

#3. **Should contain 2 or 3 #s**

#4. **Check_password, check password length,lowercase and uppercase**

#5. **Should contain (1) special character**


```python
def check_password_len(password):
    if len(password) >= 10:
        attempt = 0
        return attempt
    else:
        attempt = 1
        return attempt
def check_password_upper(password):
    for i in password:
        upper = i.isupper()
        int(upper)
        if upper == 1:
            attempt1 = 0
            return attempt1
    attempt1 = 1
    return attempt1

def check_password_lower(password):
    for i in password:
        lower = i.islower()
        int(lower)
        if lower == 1:
            attempt2 = 0
            return attempt2
    attempt2 = 1
    return attempt2
            
def check_password_digit(password):
    digit_count = 0
    for i in password:
        digit = i.isdigit()
        int(digit)
        if digit == 1:
            digit_count +=1
        if digit_count > 1:
            attempt3 = 0
            return attempt3
    attempt3 = 1
    return attempt3

def check_password_alnum(password):
    if password.isalnum():
        attempt4 = 1
        return attempt4
    else:
        attempt4 = 0
        return attempt4

def create_password():
    print("Enter Desired Password")
    print("Password Rules:")
    print("Greater than 10 Characters.")
    print("Should Contain at least one uppercase letter.")
    print("Should Contain One Special Character.")
    print("Should Contain two or three numbers.")
    password = input("Please Enter Desired Password: ")
    return password
```


```python
def check_password():
    attempt = 0
    while attempt < 3:
        attempts = 0
        pword = create_password()
        attempts = check_password_len(pword)
        if attempts > 0:
            attempt = attempt + attempts
        else:
            attempts = check_password_upper(pword)
            if attempts > 0:
                attempt = attempt + attempts
            else:
                ttempts = check_password_lower(pword)
                if attempts > 0:
                    attempt = attempt + attempts
                else:
                    attempts = check_password_digit(pword)
                    if attempts > 0:
                        attempt = attempt + attempts
                    else:
                        attempts = check_password_alnum(pword)
                        if attempts > 0:
                            attempt = attempt + attempts
                        else:
                            return pword
    return attempt

```

#3. **Allow to user to input # of students,(numbers between 1-50)**
#The system must allow the user only three attempts otherwise the program will stop.


```python
def no_of_students():
    students_count = 0
    while students_count < 3:
        students = input("Enter Number of Students:")
        students1 = students.isdigit()
        int(students1)
        if type(students1) == 0:
            students_count +=1
        else:
            students = int(students)
            if students < 1 or students > 50:
                students_count +=1
            else:
                return students
    print("YOU HAVE EXCEED THE NUMBER OF TRIES")
    exit()
```

#4. **System must ask the user to enter the names of students.**


```python
def get_students_names(students_count):
    student_names = []
    print(students_count)
    for i in range(students_count):
        student_names.append(input("Enter Student Name: "))
    return student_names
```

#5. **the system must prompt the user to enter the grades of the courses of each student as follows:**

#a-	“Input your mark in Math” Credit hours = 4 divide by the addition of these total = 22

#b-	“Input your mark in Science” Credit hours = 5

#c-	“Input your mark in Language” Credit hours = 4

#d-	“Input your mark in Drama” Credit hours = 3

#e-	“Input your mark in Music” Credit hours = 2

#f-	“Input your mark in Biology” Credit hours = 4


```python
def input_grades(students_count,students_names):
    students_grades = []
    for i in range(students_count):
        courses_grade = []
        print("***************************", students_names[i], "***************************")
        courses_grade.append(int(input("Input your mark in Math: ")))
        courses_grade.append(int(input("Input your mark in Science: ")))
        courses_grade.append(int(input("Input your mark in Language: ")))
        courses_grade.append(int(input("Input your mark in Drama: ")))
        courses_grade.append(int(input("Input your mark in Music: ")))
        courses_grade.append(int(input("Input your mark in Biology: ")))
        students_grades.append(courses_grade)
    return students_grades
```

#6. **The system must calculate the GPA of each student based on the grades that were entered in the previous step according to the following function:**
#GPA= ∑ (Mark * Credit hours)/total credit hours


```python
def calc_gpa(student_grades,credit_hours):
    gpas = []
    for i in student_grades:
        gpa1 = 0
        count = 0
        for j in i:
            gpa2 = (j * credit_hours[count])/22
            gpa1 = gpa1 + gpa2
            count += 1
        gpas.append(gpa1)
    return(gpas)
```

#7. **The system must assign students to schools based on the following matrix:**





#School of Engineering: 90 >= GPA <=100

#School of Business: 80>= GPA <90

#Law School: 70 >= GPA <80

#Not accepted: GPA <70



#8. **The system must be able to print the following:**

#a-	Report 1: Student Name, School Name 

#b-	Report 2: Number of accepted students in Humber college showing students distribution per each school.

#c-	Report 3: Number of students that not accepted.


```python
def identify_school(gpa,students_names):
    schools = [["School of Engineering"],["School of Business"],["Law School"],["Not Accepted"]]
    print(gpa)
    counter = 0

    for i in gpa:
        if gpa[counter] >= 90 and gpa[counter] <= 100:
            schools[0].append(students_names[counter])
            counter += 1
        elif gpa[counter] >=80 and gpa[counter] < 90:
            schools[1].append(students_names[counter])
            counter += 1
        elif gpa[counter] >= 70 and gpa[counter] < 80:
            schools[2].append(students_names[counter])
            counter += 1
        else:
            schools[3].append(students_names[counter])
            counter += 1
        if counter > len(students_names):
            return schools
    print(schools)        
    return schools
```


```python
def student_schools(schools):
    print("*************************************************")
    print("NAME       SCHOOL")
    for i in schools:
        k = 0
        l = 1
        for j in range(len(i)-1):
            if len(i) < 1:
                break
            else:
                print(i[j+1], " ", i[k])
```


```python
def accepted_students(schools):
    print("*************************************************")
    total_accepted = 0
    for i in schools:
        if i[0] == "Not Accepted" or len(i) == 1:
            pass
        else:
            total_accepted = total_accepted + (len(i)-1)
    print("Total Accepted Students:",total_accepted)
    
    for i in schools:
        if i[0] == "Not Accepted":
            pass
        else:
            print(i[0],":",len(i)-1)

    for i in schools:
        if i[0] != "Not Accepted":
            pass
        else:
            print("Number of Not Accepted Students:",len(i)-1)
```


```python
def get_waitlist(gpa,students_names):
    #initialize the names and gpas candidate for waitlist
    waitlist_names = []
    waitlist_gpa = []
    #counter to track the index of the names and gpas that are candidate for waitlist
    student_namegpa_counter = 0
    #loop for finding the gpas < 70
    for i in gpa:
        if i < 70:
            #append the names and gpas of students who are candidate for waitlist
            waitlist_names.append(students_names[student_namegpa_counter])
            waitlist_gpa.append(gpa[student_namegpa_counter])
        #increment the index counter for names and gpas
        student_namegpa_counter += 1
    #create list for the index which will be used to track the student name and gpa
    waitlist_index = []
    #populate the list
    for i in range(len(waitlist_gpa)):
        waitlist_index.append(i)
    #create a copy of the waitlist gpa and use it for sorting
    waitlist_gpa1 = waitlist_gpa.copy()
    #after getting the list of names and gpas need to sort it
    #sorting algorithm
    n = 1
    for i in range(len(waitlist_gpa1)):
        for j in range(n,len(waitlist_gpa1)):
            temp1 = 0
            temp = 0
            if waitlist_gpa1[j] > waitlist_gpa1[i]:
                temp1 = waitlist_gpa1[i]
                waitlist_gpa1[i] = waitlist_gpa1[j]
                waitlist_gpa1[j] = temp1
                temp = waitlist_index[i]
                waitlist_index[i] = waitlist_index[j]
                waitlist_index[j] = temp
        n += 1
    #Printing the waitlisted students
    print("****************Waitlisted********************")
    print("Name     GPA")
    
    if len(waitlist_gpa) <= 3:
        for i in waitlist_index:
            print(waitlist_names[i],"   ",waitlist_gpa[i])
    else:
        for i in range(3):
            print(waitlist_names[waitlist_index[i]],"   ",waitlist_gpa[waitlist_index[i]])
            
    return 0
```

#check if the returned value of check_password is str or int if string the password met the criteria and program will continue


```python
def welcome_message():

    user_password = check_password() #check if the returned value of check_password is str or int if string the password met the criteria and program will continue
    if type(user_password) == str:
            print("Password Created")
    else:
            print("YOU HAVE EXCEEDED THE NUMBER OF TRIES")
            exit()

    enter_password = input("What's the Password?")

    if enter_password == user_password:
            print("You have input the correct password")
    else:
            print("Wrong Password BYE")
```

#call the check_password function and check if the password entered by user met the criteria

#call the function that will ask for no. of students


```python
students_count = no_of_students()
```

#call the function that will ask for students names


```python
students_names = get_students_names(students_count)
```

#call the function that will ask for grades using students_count and students_names as input


```python
student_grades = input_grades(students_count,students_names)
```


```python
print(student_grades)
```

#create a list for credit hours


```python
credit_hours = [4,5,4,3,2,4]
```

#call the function that will calculate the gpa using student_grades and credit_hours as input


```python
gpa = calc_gpa(student_grades,credit_hours)
```

#call the function that will distribute students to different school



```python
schools = identify_school(gpa,students_names)
```

#call the function that will print the student name and their corresponding school


```python
print_school_student = student_schools(schools)
```

#call the function that will calculate the number of accepted students


```python
total_accepted = accepted_students(schools)
```

#call the function that will get 3 students that are waitlisted


```python
get_waitlist(gpa,students_names)
```

Testing - Password Requirement

![Team%2015%20Group%20Project%20%282%29.png](attachment:Team%2015%20Group%20Project%20%282%29.png)

Student Grades

![student-grades.png](attachment:student-grades.png)

Reports

![Team%2015%20Group%20Project%20%284%29.png](attachment:Team%2015%20Group%20Project%20%284%29.png)

Additional Report

![Team%2015%20Group%20Project%20%281%29.png](attachment:Team%2015%20Group%20Project%20%281%29.png)
