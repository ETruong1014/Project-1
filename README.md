# proj1F20
This project makes use of two different classes to perform two different tasks.
The class DataTimeOne is simply used to output the current time, the second value of the current time, and making the program sleep if the second value is greater than 30.
The class HammingDistance takes two STIDs and finds the hamming distancebetween them and NRMN, as well as finding the total number of stations in Mesonet.txt with the same hamming distances.

## DateTimeOne

The method implementations for DateTimeOne are generally very simple. 
The method `getValueOfSecond()` uses a print statement to print out the second value of the current time.
It then returns that value as an int.
The method `sleepForThreeSec()` has the program sleep for 3000 milliseconds, or 3 seconds, when it is called.

## HammingDistance

HammingDistance requires 3 non-constructor methods to accomplish its tasks. 
A HammingDistance object has instance variables of station1, station2, hamm1, hamm2, numStations1, and numStations2.
station1 and station2 are the two stations that a new object passes as a parameter.
hamm1 and hamm2 are the hamming distances between the parameter stations and NRMN. 
numStations1 and numStations2 are the number of stations from the file that have the same hamming distance as the two parameter stations and NRMN.

### HammingDistance Constructor

The constructor takes the two parameters station1 and station2 and assigns them to the instance variables of the same name.
It then calls upon two other methods in order to assign values to the hamming distances and the number of stations.

### nrmnHamm

The method `nrmnHamm` takes a String parameter that is the station to be compared to NRMN.
A variable hammNum is created that represents the hamming distance.
The method then goes througha for-loop that compares the characters of the parameter string to NRMN, incrementing hammNum by 1 each time the characters differ. 
As the strings to be compared are always 4 characters, the loop runs 4 times, comparing characters at indexes 0 to 3.
The method will then return the int value hammNum.

### hammStations

The method `hammStations` is what is used to find the number of stations with the same hamming distance as the input station.
It takes two parameters, one being a String representing the input station, and the other being an int value representing the hamming distance found using nrmnHamm.
The method creates FileInputStream and Scanner objects to read Mesonet.txt. 
The method also creates other variables, such as numStations to keep track of the total number stations in the file, hammNum to use to compare hamming distances, and numSameDist to keep track of how many stations have the same hamming distance as the input station's.
The method also creates a String array called fileStations to store the stations from Mesonet.txt.

#### Comparing STIDs

After opening the file, a for-loop will have the scanner skip past the first 5 lines in Mesonet.txt, as the STIDs only start on line 6. 
A while-loop will then read lines until the end of the file. 
Each line, the scanner will add the STID on the line, then skip to the next line. 
It will double the size of the array if it is full, along with incrementing numStations by 1 every time a station is added.
The method will then use a for-loop nested inside another for-loop for comparing stations.
The outermost loop will loop for whatever the value of numStations is, as it will go through every station in Mesonet.txt.
The inner for-loop does the same thing that hammStations does, and compared hamming distances of the current station to the parameter station. 
If they have the same hamming distance as the parameter station's NRMN hamming distance, numSameDist will be incremented by 1. 
After every STID has been compared, the file will close and return numSameDist.

### toString

The `toString` method will simply return a string that contains the hamming distances between NRMN and the object's two stations, as well as the number of stations that have the same hamming distance.
