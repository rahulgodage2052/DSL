#include <iostream>
#include <queue>
#include <string>
using namespace std;

struct Patient {
    string name;
    int priority;

    // Define comparison operator for priority_queue
    bool operator<(const Patient& p) const {
        // Higher priority number = higher urgency
        return priority < p.priority;
    }
};

int main() {
    priority_queue<Patient> pq;
    int n;

    cout << "Enter the number of patients: ";
    cin >> n;

    for (int i = 0; i < n; i++) {
        Patient p;
        cout << "\nEnter patient name: ";
        cin >> p.name;
        cout << "Enter priority (3 - Serious, 2 - Non-Serious, 1 - General Checkup): ";
        cin >> p.priority;
        pq.push(p);
    }

    cout << "\nServing patients in priority order:\n";
    while (!pq.empty()) {
        Patient p = pq.top();
        pq.pop();
        cout << "Serving " << p.name << " (Priority: " << p.priority << ")\n";
    }

    return 0;
}
