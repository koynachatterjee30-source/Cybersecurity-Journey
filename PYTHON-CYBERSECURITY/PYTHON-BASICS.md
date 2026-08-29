# Python Basics for Cybersecurity

Python is a high-level programming language widely used in cybersecurity for automation, network programming, security testing, log analysis, data processing, and developing security tools.

## 1. Variables and Data Types

Variables store information in a program .

```python
name = "koyna"
age = 21
ip = "192.168.1.10"
port = 80
active = True


ip = input("Enter IP address: ")
print("Target IP:", ip)

a = 10
b = 5

print(a + b)
print(a - b)
print(a * b)
print(a / b)

print(a == b)
print(a != b)
print(a > b)



and
or
not

port = 80

if port == 80:
    print("HTTP")
elif port == 443:
    print("HTTPS")
else:
    print("Other port")

for port in range(1, 6):
    print(port)

count = 1

while count <= 5:
    print(count)
    count += 1

def check_port(port):
    print("Checking port:", port)

check_port(80)

ports = [21, 22, 80, 443]

for port in ports:
    print(port)

user = {
    "username": "admin",
    "role": "administrator",
    "active": True
}

print(user["username"])

with open("logs.txt", "r") as file:
    data = file.read()

print(data)

try:
    number = int(input("Enter a number: "))
    print(number)
except ValueError:
    print("Invalid input")

