# Ex02 Django ORM Web Application
## Date: 
4/10/2024
## AIM
To develop a Django application to store and retrieve data from a bank loan database using Object Relational Mapping(ORM).

## ENTITY RELATIONSHIP DIAGRAM



## DESIGN STEPS

### STEP 1:
Clone the problem from GitHub

### STEP 2:
Create a new app in Django project

### STEP 3:
Enter the code for admin.py and models.py

### STEP 4:
Execute Django admin and create details for 10 books

## PROGRAM
admin.py :
```
from django.contrib import admin
from .models import Customer, Loan

admin.site.register(Customer)
admin.site.register(Loan)
```
models.py :
```
from django.db import models

class Customer(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    phone_number = models.CharField(max_length=15)

    def __str__(self):
        return self.name


class Loan(models.Model):
    LOAN_STATUS = [
        ('P', 'Pending'),
        ('A', 'Approved'),
        ('R', 'Rejected'),
    ]
    
    loan_id = models.AutoField(primary_key=True)
    customer = models.ForeignKey(Customer, on_delete=models.CASCADE)
    loan_amount = models.DecimalField(max_digits=10, decimal_places=2)
    loan_term = models.IntegerField()  # Loan term in months
    interest_rate = models.DecimalField(max_digits=4, decimal_places=2)
    status = models.CharField(max_length=1, choices=LOAN_STATUS, default='P')
    issued_date = models.DateField(auto_now_add=True)

    def __str__(self):
        return f"Loan {self.loan_id} - {self.customer.name}"
```


## OUTPUT

![Screenshot (1)](https://github.com/user-attachments/assets/14a5a994-59a8-43ae-8f5b-071fbfea47a4)



## RESULT
Thus the program for creating a database using ORM hass been executed successfully
