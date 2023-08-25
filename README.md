#include <iostream>
#include <string>
#include <vector>

// Contact class to store individual contact information
class Contact {
public:
    Contact(const std::string& name, const std::string& phoneNumber)
        : name(name), phoneNumber(phoneNumber) {}

    // Getter methods to access contact information
    std::string getName() const {
        return name;
    }

    std::string getPhoneNumber() const {
        return phoneNumber;
    }

private:
    std::string name;
    std::string phoneNumber;
};

// ContactManager class to manage a list of contacts
class ContactManager {
public:
    // Add a new contact to the list
    void addContact(const std::string& name, const std::string& phoneNumber) {
        contacts.push_back(Contact(name, phoneNumber));
    }

    // Display all contacts
    void displayContacts() const {
        std::cout << "Contacts:" << std::endl;
        for (const Contact& contact : contacts) {
            std::cout << "Name: " << contact.getName() << ", Phone: " << contact.getPhoneNumber() << std::endl;
        }
    }

private:
    std::vector<Contact> contacts; // Vector to store contacts
};

int main() {
    ContactManager contactManager; // Create an instance of ContactManager

    char choice;
    do {
        std::string name, phoneNumber;

        // Get contact information from the user
        std::cout << "Enter contact name: ";
        std::cin >> name;

        std::cout << "Enter phone number: ";
        std::cin >> phoneNumber;

        // Add the contact to the manager
        contactManager.addContact(name, phoneNumber);

        // Ask if the user wants to add another contact
        std::cout << "Do you want to add another contact? (y/n): ";
        std::cin >> choice;
    } while (choice == 'y' || choice == 'Y');

    // Display all contacts
    contactManager.displayContacts();

    return 0;
}
