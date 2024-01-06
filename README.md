#include <stdio.h>

// Enum for marital status
enum MaritalStatus {
    SINGLE,
    MARRIED,
    WIDOW,
    DIVORCED
};

// Structure to hold information based on marital status
struct Person {
    enum MaritalStatus status;
    union {
        struct {
            int marriageYear;
            int marriageMonth;
            int marriageDay;
        } marriedInfo;

        struct {
            int deathYear;
            int deathMonth;
            int deathDay;
        } widowInfo;

        struct {
            int divorceYear;
            int divorceMonth;
            int divorceDay;
        } divorcedInfo;
    };
};

int main() {
    // Example usage
    struct Person person;

    // Set marital status
    person.status = MARRIED;

    // Set information based on marital status
    switch (person.status) {
        case MARRIED:
            person.marriedInfo.marriageYear = 2020;
            person.marriedInfo.marriageMonth = 6;
            person.marriedInfo.marriageDay = 15;
            break;

        // Additional cases for WIDOW and DIVORCED can be added similarly

        default:
            break;
    }

    // Access information based on marital status
    switch (person.status) {
        case MARRIED:
            printf("Marriage Date: %d-%02d-%02d\n",
                   person.marriedInfo.marriageYear,
                   person.marriedInfo.marriageMonth,
                   person.marriedInfo.marriageDay);
            break;

        // Additional cases for WIDOW and DIVORCED can be added similarly

        default:
            break;
    }

    return 0;
}
