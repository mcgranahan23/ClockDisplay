//
//  main.cpp
//  InternationalClock
//
//  Created by Miles Mcgranahan on 7/11/24.
//

#include <iostream>
#include <iomanip>
using namespace std;


string userTime;
int hour, hr24, hr12;
int mins;
int sec;
char colon, nightDay;
bool proceed = false;
int amPM, menuSelect;
bool menu = false;



int hour24(int hr, bool time) {
    // time = true means PM
    if (hr < 12 && time) {
        hr = hr + 12;
    }
    return hr;
}
int hour12(int hr) {
    hr = hr - 12;
    return hr;
}
// zone: 24 or 12 hour
// type: 1 - Hour, 2 - Minute, 3 - Second
// current: current time
// amount: amount added
int changeTime(int zone, int type, int current) {
    
    if (zone == 12){
        switch (type) {
            case 1:
                if ((current + 1) > 12) {
                    current = (current + 1) - 12;
                    return current;
                    break; }
                else { cout << current << endl;
                    current = current + 1;
                    return current;
                    break; }
            case 2:
                if ((current + 1) > 59) {
                    current = (current + 1) - 60;
                    return current;
                    break; }
                else { current = current + 1;
                    return current;
                    break; }
            case 3:
                if ((current + 1) > 59) {
                    current = (current + 1) - 60;
                    return current;
                    break; }
                else { current = current + 1;
                    return current;
                    break; }
        }
    }
    
    if (zone == 24) {
        switch (type) {
            case 1:
                if ((current + 1) > 23) {
                    current = (current + 1) - 24;
                    return current;
                    break; }
                else { current = current + 1;
                    return current;
                    break; }
            case 2:
                if ((current + 1) > 59) {
                    current = (current + 1) - 60;
                    return current;
                    break; }
                else { current = current + 1;
                    return current;
                    break; }
            case 3:
                if ((current + 1) > 59) {
                    current = (current + 1) - 60;
                    return current;
                    break; }
                else { current = current + 1;
                    return current;
                    break; }
        }
    }
    type = 0;
    return 0; }
void showMenu() {
    cout << setfill('*') << setw(30) << "" << endl;
    cout << "*\t" << "1.) Add one hour\t\t" << " *" << endl;
    cout << "*\t" << "2.) Add one minute\t\t" << " *" << endl;
    cout << "*\t" << "3.) Add one second\t\t" << " *" << endl;
    cout << "*\t" << "4.) Exit\t" << "\t\t\t *" << endl;
    cout << setfill('*') << setw(30) << "" << endl;
}
void display24(int hrs, int mins, int sec) {
    cout << setfill('*') << setw(21) << "" << endl;
    cout << "*\t24 Hour Clock\t*" << endl;
    cout << "*\t  " << setfill('0') << setw(2) << hrs << ":" << setfill('0') << setw(2) << mins << ":" << setfill('0') << setw(2) << sec << right << setw(7) << setfill(' ') << "*" << endl;
    cout << setfill('*') << setw(22) << "\n" << endl;
}
void display12(int hrs, int mins, int sec, char amPM) {
    cout << setfill('*') << setw(21) << "" << endl;
    cout << "*\t12 Hour Clock\t*" << endl;
    cout << "*\t " << setfill('0') << setw(2) << hrs << ":" << setfill('0') << setw(2) << mins << ":" << setfill('0') << setw(2) << sec << " " << amPM << "M" << right << setw(5) << setfill(' ') << "*" << endl;
    cout << setfill('*') << setw(22) << "\n" << endl;
    hrs = 0;
}


int main() {
    while (!proceed) {
        try {
            cout << "Please enter an initial start time in format 00:00:00 " << endl;
            cin >> hour;
            cin >> colon;
            cin >> mins;
            cin >> colon;
            cin >> sec;
            if (isdigit(colon) || isalpha(colon)) { throw ("Invalid colon input."); }
            if (hour > 24 || hour < 0) { throw ("Invalid hour input."); }
            if (mins > 59 || mins < 0) { throw ("Invalid minute input."); }
            if (sec > 59 || sec < 0) { throw ("Invalid second input."); }
            //if (isdigit(colon) || isalpha(colon)) { throw ("Invalid colon input."); }
            else { proceed = true; }
            cout << endl;
        }
        catch  (...) { cin.clear();
            cin.ignore(100, '\n'); }
    }
    // For 24 hour clock
    while (proceed) {
        if (hour < 13) { cout << "Is it AM or PM? Enter 1 or 2: \n1.) AM \n2.) PM \n" << endl;
            cin >> amPM;
            if (amPM == 1) { hr24 = hour;
                proceed = false;
                nightDay = 'A'; } // If it's AM it won't be past 12, no need for function
            else if (amPM == 2) { hr24 = hour24(hour, true); // All PMs in 24 hr are past 12
                nightDay = 'P';
                proceed = false; }
            else { cout << "Invalid selection, enter 1 or 2.";
                cin.clear();
                cin.ignore(10, '\n'); }
        } if (hour > 12) { hr24 = hour;
            hour = hour12(hour);
            nightDay = 'P';
            proceed = false; }
    }

    
    display24(hr24, mins, sec);
    display12(hour, mins, sec, nightDay);

    while (!menu) {
        showMenu();
        cout << "Please enter a number 1-4. ";
        cin >> menuSelect;
        
        switch (menuSelect) { // menu: 1 - add 1 hour - 2 - add min - 3 add sec - 4 exit
            case 1:
                if (hour == 11) {
                    if (nightDay == 'P') { nightDay = 'A'; }
                    else { nightDay = 'P'; }
                }
                hour = changeTime(12, 1, hour);
                hr24 = changeTime(24, 1, hr24);
                display24(hr24, mins, sec);
                display12(hour, mins, sec, nightDay);
                
                break;
            case 2:
                if (mins == 59) {
                    if (hour == 12) { hour = 1; }
                    else if (hour == 11 && nightDay == 'P') { hour = hour + 1;
                        nightDay = 'A'; }
                    else if (hour == 11 && nightDay == 'A') { hour = hour + 1;
                        nightDay = 'P'; }
                    else { hour = hour + 1; }
                }
                if (mins == 59 && hr24 == 23) {
                    hr24 = 0;
                } else { hr24 = hr24 + 1; }
                
                mins = changeTime(12, 2, mins);
                display24(hr24, mins, sec);
                display12(hour, mins, sec, nightDay);
                break;
            case 3:
                if (sec == 59) {
                    if (mins == 59) { mins = 0;
                       
                        if (hour == 11 && nightDay == 'P') { ++hour;
                            nightDay = 'A'; }
                        else if (hour == 11 && nightDay == 'A') { ++hour;
                            nightDay = 'P'; }
                        else if (hour != 11 && hour != 12) { ++hour; }
                        if (hr24 == 23) { hr24 = 0; }
                        else { ++hr24; }
                        if (hour == 12) { hour = 1; }
                    }
                    else if (mins != 59) { ++mins; }
                    
                    
                }
                sec = changeTime(12, 3, sec);
                display24(hr24, mins, sec);
                display12(hour, mins, sec, nightDay);
                break;
            case 4:
                cout << "Goodbye" << endl;
                menu = true;
                
                break;
            default:
                cout << "Invalid selection, enter 1, 2, 3, or 4.";
                cin.clear();
                cin.ignore(10, '\n');
                break;
        }
        cin.clear();
        cin.ignore(10, '\n');
    }
    menu = true;
    // zone: 24 or 12 hour
    // type: 1 - Hour, 2 - Minute, 3 - Second
    // current: current time
    // amount: amount added
    //int changeTime(int zone, int type, int current, int amount)
    
    
    return 0;
}
