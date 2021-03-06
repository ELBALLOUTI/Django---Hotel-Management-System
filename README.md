# Django - Hotel Management System
* Requirement Analysis Document - System Design Document - Object Design Document - Mockups - Class Diagram - ER Diagram are in the "Documents" Folder

* This is a hotel management system that has 5 different user types: <br>
Admin - Manager - Receptionist - Staff - Guest  (Each of the types have different permissions and functionalities.) 

* There are some screenshots of the program in the "Screenshots" folder.

### In order to download and run the project ( Python 3 needs to be installed ):
1. Install Django and related Apps:
```shell
pip install Django==3.1.4
pip install django-phonenumber-field[phonenumbers]
```
## Needed to create roles and admin account to add new employee accounts
2. Change Directory to Django---Hotel-Management-System/HMS and start the Shell:
```shell
python3 manage.py shell
```
* Then execute these, one by one:
```shell
from django.contrib.auth.models import Group, User
```

```shell
from accounts.models import Employee
```

```shell
Group.objects.create(name='admin')
```

```shell
Group.objects.create(name='manager')
```

```shell
Group.objects.create(name='receptionist')
```

```shell
Group.objects.create(name='staff')
```

```shell
Group.objects.create(name='guest')
```

```shell
user = User.createuser=User.objects.create_user('admin', password='admin123')
```

```shell
group = Group.objects.get(name="admin")
```

```shell
user.groups.add(group)
```

```shell
admin = Employee(user=user, salary=0)
```

```shell
admin.save()
```

### Finally:
* Exit the shell and set the database: 
```shell
python3 manage.py makemigrations
python3 manage.py migrate
```
Then, start the server
```shell
python3 manage.py runserver
```

## Notes:
#### Note 1: In the program, there is a payment page. No need to enter real credit-card informations as this page is just for demostration purposes only. After this page, a verification code is sent to the user's email address.


#### Note 2: You can only sign up as a guest to the system. In order to add employee (Manager - Receptionist - Staff): 
* Login into the system with username: "admin" and password : "admin123"
* Go the employee's page in options dropdown menu in navbar.
* Click "Add New Employee" button, fill the form and save it.
* You will see a success message. Then, you can use that employee's information to enter the system.


#### Note 3: For the email system (In some cases the system sends e-mails):
* Go to the HMS/setting.py
* Under the settings file you can find the email settings, uncomment them in order to change the settings and put the email address you want to use to receive the emails from the system.
