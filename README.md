import random

class Employee:
    def _init_(self, emp_id, name, salary, revenue_generated):
        self.emp_id = emp_id
        self.name = name
        self.salary = salary
        self.revenue_generated = revenue_generated

    def _str_(self):
        return f"ID: {self.emp_id}, Name: {self.name}, Salary: ${self.salary}, Revenue: ${self.revenue_generated}"

class Company:
    def _init_(self):
        self.employees = []

    def add_employee(self, employee):
        self.employees.append(employee)

    def total_expenditure(self):
        return sum(emp.salary for emp in self.employees)

    def total_revenue(self):
        return sum(emp.revenue_generated for emp in self.employees)

    def net_profit(self):
        return self.total_revenue() - self.total_expenditure()

    def generate_report(self):
        print("----- Company Financial Report -----")
        print(f"Total Employees: {len(self.employees)}")
        print(f"Total Expenditure: ${self.total_expenditure():,.2f}")
        print(f"Total Revenue: ${self.total_revenue():,.2f}")
        print(f"Net Profit: ${self.net_profit():,.2f}")
        print("------------------------------------")

# Create company instance
company = Company()

# Generate 200 employees with random salary and revenue
for i in range(1, 201):
    name = f"Employee_{i}"
    salary = random.randint(30000, 100000)
    revenue_generated = random.randint(40000, 150000)
    emp = Employee(emp_id=i, name=name, salary=salary, revenue_generated=revenue_generated)
    company.add_employee(emp)

# Display the report
company.generate_report()
