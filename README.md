# Django - Hotel Management System
* Requirement Analysis Document - System Design Document - Object Design Document are in the "Documents" Folder <br>

It is hotel management system which have 5 different user types: <br>
Admin - Manager - Receptionist - Staff - Guest  (Each of the types have different functionality.) <br>


### In order to download and run the project ( It is assumed that Python 3 is already installed ):
1. Install Django and Apps:
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
Then, start the surver
```shell
python3 manage.py runserver
```
* This will work if correctly set up.

## Notes:
#### Note1: In the program, there are some payment page. No need to enter real credit-card informations. The payment page just for the system, it doesnt work. However; after these page, a verification code is sent the user mail address.


#### Note 2: You can only sign up as a guest to the system. In order to add employee (Manager - Receptionist - Staff): 
* login in to the system with username: "admin" and password : "admin123"
* Go the employee page on options in navbar.
* Click "Add New Employee" button, fill the form and send it.
* You will see the success message. After then, you can use that employee to enter the system 


#### Note 3: For the mail system works (In some case system sends e-mails):
* Go to the HMS/setting.py
* Under of the file mail settings are as command lines. Put out of them from command and change the setting according to your mail address
