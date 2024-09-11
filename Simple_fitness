#include <iostream>
#include <cmath>
#include <string>

using namespace std;

class User {
private:
    string username;
    string password;

public:
    User(string name, string pass) : username(name), password(pass) {}

    bool authenticate(string user, string pass) {
        return (username == user && password == pass);
    }

    string& getUsername() {
        return username;
    }
};

class Activity {
protected:
    User* user;

public:
    Activity(User* u) : user(u) {}

    virtual void perform() = 0;

    virtual ~Activity() {}
};

class StepsActivity : public Activity {
public:
    StepsActivity(User* u) : Activity(u) {}

    void perform()  {
        int steps;
        cout << "Enter the number of steps taken: ";
        cin >> steps;

        double caloriesBurned = steps * 0.05;
        cout << "Calories burned: " << caloriesBurned << " kcal" << endl;
    }
};

class BmiActivity : public Activity {
public:
    BmiActivity(User* u) : Activity(u) {}

    void perform()  {
        double height, weight;
        cout << "Enter your height (in meters): ";
        cin >> height;
        cout << "Enter your weight (in kilograms): ";
        cin >> weight;

        double bmi = weight / pow(height, 2);
        cout << "Your BMI is: " << bmi << endl;
    }
};

class CyclingActivity : public Activity {
public:
    CyclingActivity(User* u) : Activity(u) {}

    void perform()  {
        double duration;
        cout << "Enter the duration of cycling (in minutes): ";
        cin >> duration;

        double caloriesBurned = duration * 8;
        cout << "Calories burned: " << caloriesBurned << " kcal" << endl;
    }
};

class SwimmingActivity : public Activity {
public:
    SwimmingActivity(User* u) : Activity(u) {}

    void perform()  {
        double duration;
        cout << "Enter the duration of swimming (in minutes): ";
        cin >> duration;

        double caloriesBurned = duration * 10;
        cout << "Calories burned: " << caloriesBurned << " kcal" << endl;
    }
};

class FitnessApp {
private:
    User* user;

public:
    FitnessApp(User* u) : user(u) {}

    void start() {
        char choice;
        do {
            cout << "\nFitness App Menu" << endl;
            cout << "1. Step Counting" << endl;
            cout << "2. BMI Calculation" << endl;
            cout << "3. Cycling" << endl;
            cout << "4. Swimming" << endl;
            cout << "5. Exit" << endl;
            cout << "Enter your choice: ";
            cin >> choice;

            switch (choice) {
                case '1': {
                    StepsActivity stepsActivity(user);
                    stepsActivity.perform();
                    break;
                }
                case '2': {
                    BmiActivity bmiActivity(user);
                    bmiActivity.perform();
                    break;
                }
                case '3': {
                    CyclingActivity cyclingActivity(user);
                    cyclingActivity.perform();
                    break;
                }
                case '4': {
                    SwimmingActivity swimmingActivity(user);
                    swimmingActivity.perform();
                    break;
                }
                case '5': {
                    cout << "Exiting Fitness App. Goodbye!" << endl;
                    return;
                }
                default:
                    cout << "Invalid choice. Please try again." << endl;
            }
        } while (true);
    }
};

int main() {
    User* user;

    int choice;
    cout << "Welcome to Fitness App!" << endl;
    cout << "1. Login" << endl;
    cout << "2. Create New Account" << endl;
    cout << "Enter your choice: ";
    cin >> choice;

    if (choice == 1) {
        string username, password;
        cout << "Enter username: ";
        cin >> username;
        cout << "Enter password: ";
        cin >> password;
        user = new User(username, password);

        if (!user->authenticate(username, password)) {
            cout << "Invalid username or password. Exiting..." << endl;
            delete user;
            return 1;
        }
    } else if (choice == 2) {
        string newUsername, newPassword;
        cout << "Enter new username: ";
        cin >> newUsername;
        cout << "Enter new password: ";
        cin >> newPassword;
        user = new User(newUsername, newPassword);
        cout << "Account created successfully! Welcome, " << user->getUsername() << "!" << endl;
    } else {
        cout << "Invalid choice!" << endl;
        return 1;
    }

    FitnessApp app(user);
    app.start();

    delete user;

    return 0;
}
