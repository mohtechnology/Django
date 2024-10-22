# Creating Admin User
#### First We Need To Migrate
```bash
python manage.py migrate
```
#### Now We Can Access The Admin Panel
## Creating Super User
```bash
python manage.py createsuperuser
```
```bash
Username (leave blank to use 'mohsh'): moh
Email address:
Password:
Password (again):
Superuser created successfully.
```
## Changing Super User Password
```bash
python .\manage.py changepassword moh
```
```bash
Changing password for user 'moh'
Password: 
Password (again): 
Password changed successfully for user 'moh'
```
