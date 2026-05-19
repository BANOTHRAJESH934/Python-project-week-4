# Python-project-week-4
This Python program is an Intelligent Testing System developed using Object-Oriented Programming (OOP) concepts. The system combines multiple functionalities such as user management, decision-making, data processing, system state control, and performance analysis.

Code:
import random
import time

class UserSystem:
    def __init__(self):
        self.users = {}

    def register(self, username, password):
        if username in self.users:
            print("User already exists!")
        else:
            self.users[username] = password
            print("Registration Successful!")

    def login(self, username, password):
        if username in self.users and self.users[username] == password:
            print("Login Successful!")
            return True
        else:
            print("Invalid Username or Password")
            return False

class DecisionEngine:
    def __init__(self):
        self.rules = {
            "rain": "Take an umbrella",
            "sunny": "Wear sunglasses",
            "cold": "Wear a jacket",
            "exam": "Start studying",
            "hungry": "Eat healthy food"
        }

    def make_decision(self, condition):
        return self.rules.get(condition.lower(), "No decision found")

class DataProcessor:
    def process_data(self, data):
        print("\nProcessing Data...")
        time.sleep(1)

        total = sum(data)
        average = total / len(data)

        print("Total:", total)
        print("Average:", average)

        return total, average

class SystemState:
    def __init__(self):
        self.current_state = "IDLE"

    def update_state(self, new_state):
        print(f"Changing State: {self.current_state} -> {new_state}")
        self.current_state = new_state

class PerformanceAnalyzer:
    def analyze(self):
        print("\nAnalyzing System Performance...")
        cpu_usage = random.randint(20, 90)
        memory_usage = random.randint(30, 95)

        print("CPU Usage:", cpu_usage, "%")
        print("Memory Usage:", memory_usage, "%")

        if cpu_usage > 80:
            print("Warning: High CPU Usage")

        if memory_usage > 85:
            print("Warning: High Memory Usage")

class IntelligentSystem:
    def __init__(self):
        self.user_system = UserSystem()
        self.decision_engine = DecisionEngine()
        self.data_processor = DataProcessor()
        self.state_manager = SystemState()
        self.performance = PerformanceAnalyzer()

    def start(self):
        print("")
        print(" INTELLIGENT TESTING SYSTEM ")
        print("")

        username = input("Enter Username: ")
        password = input("Enter Password: ")

        self.user_system.register(username, password)

        print("\nPlease Login")

        login_user = input("Username: ")
        login_pass = input("Password: ")

        if self.user_system.login(login_user, login_pass):

            self.state_manager.update_state("ACTIVE")

            print("\nDecision Engine")
            condition = input("Enter Condition: ")
            decision = self.decision_engine.make_decision(condition)

            print("Decision:", decision)

            numbers = [10, 20, 30, 40, 50]
            self.data_processor.process_data(numbers)

            self.performance.analyze()

            self.state_manager.update_state("COMPLETED")

            print("\nSystem Execution Completed Successfully!")

if __name__ == "__main__":
    system = IntelligentSystem()
    system.start()
