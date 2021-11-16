Goal: write a method that converts arabic numerals to roman numerals
Definitions: define what a roman numeral is

1 = I

5 = V
9 = IX
10 = X
50 = L
100 = C
500 = D
1000 = M

            define what rules make a roman numeral equivelant to an arabic numeral (can't have 4 of the same numeral in a row, lower numeral in front of a higher numeral instead (4 = IV not IIII))
Limititations: 7 letters represent roman numerals. Upper limit on what can be counted with roman numerals (3,999)
Requirements: convert an integer into a string of roman numerals that portrays the same value
              takes a whole number and and converts it to the roman numeral equivelent

mechanics: seperate 1s, 10s, 100s and 1000s (1 thounand 5 hundreds  4 tens and 6 ones = 1546)
          identifies when a number is less than or equal to 3999 (done)
          defines roman numerals
          identifies when a number is greater than or equal to 1
          identifies when a number has a decimal


Describe: isValid(theArgument) 
purpose: to check if a number is in the valid range of what can be a roman numeral
When to use: as a conditional so that if it returns true then we proceed with the rest of the program, otherwise we don't proceed

Test: check if a numbers is greater or equal to 1. 
Code: 
theArgument = 0
let isItValid = false;
if(theArgument >= 1)
  isItValid = true;
  return isItValid;
  } else {
    isItValid = false;
    return isItValid;
  }
expected output: false


Test: check if a numbers is greater than or equal 1. (duplicate test with different input)
Code: 
theArgument = 4
let isItValid = false;
if(theArgument >= 1){
  isItValid = true;
  return isItValid;
  } else {
    isItValid = false;
    return isItValid;
  }
expected output: true

Test: check if a number is less than or equal to 3999
Code:
theArgument =  4001
let isItValid = false;
if(theArgument <= 3999){
  isItValid = true;
  return isItValid;
} else{
  isItValid = false;
  return isItValid;
}
Expected output: false

Test: check if a number is less than or equal to 3999 (duplicate test with different input)
Code:
theArgument =  2000
let isItValid = false;
if(theArgument <= 3999){
  isItValid = true;
  return isItValid;
} else{
  isItValid = false;
  return isItValid;
}
Expected output: true


test: check if a number is greater than or equal to 1 AND less than or equal 3999
Code:
theArgument = 0
let isItValid = false;
if(theArgument >= 1 && theArgument <= 3999){
  isItValid = true;
  return isItValid;
} else {
  isItValid = false;
  return isItValid;
}
Expected outcome: false

test: check if a number is greater than or equal to 1 AND less than or equal 3999 (duplicate test with different input)
Code:
theArgument = 250
let isItValid = false;
if(theArgument >= 1 && theArgument <= 3999){
  isItValid = true;
  return isItValid;
} else {
  isItValid = false;
  return isItValid;
}
Expected outcome: true

_______________________________________

Describe howManyThousands(theArgument)
Pupose: to return how many thousands there are in a number

test: return how many thousands there are
theArgument: 3050
let theValue = 0;
  theValue = parseInt(theArgument /1000);
  return theValue;
} 
Expected output: 3

test: return how many thousands there are (duplicate test with different input)
theArgument: 555
let theValue = 0;
  theValue = parseInt(theArgument /1000); // we use parseInt to change the value of theArgument does not have any decimal places. division returns a float and we want an integer.
  return theValue;
} 
Expected output: 0
_________________________________________________________________________________________________________
Describe howManyHundreds(theArgument)

test: remove the thousands digit
Code:
theArgument = 1500
let theValue = theArgument % 1000; //We use mod to get the remainder of theArgument essentially removing the thousands digit (1500 % 1000 = 500)
return theValue;
Expected output: 500

test: how many hundreds are there in the hundreds digit with no decimals
Code:
theArgument =1500;
let theValue = parseInt((theArgument % 1000) / 100) 

a less compact way of putting the above line is:
let theValue = theArgument % 1000)
theValue = theValue / 100. (this is saying we will set theValue to the current value of theValue / 100)
theValue = parseInt(theValue);
) We don't have to write it all out this way but sometimes more comapct code is harder to understand so I put this here as a break down

Expected output: 5
__________________________________________________________
Describe howManyTens(theArgument)

test: remove the thousands and hundreds place with no decimals
Code: 
theArgument = 1550; 
let theValue = parseInt(((theArgument % 1000) % 100));
Expected output: 50


test: output how many tens there are excluding 1000s and 100s
Code:
theArgument = 1550;
let theValue = parseInt(((theArgument % 1000) % 100) / 10);
Expected output: 5
_______________________________________________________________
describe howManyOnes(theArgument)

test: remove the 1000s 100s and 10s which will give us how many ones there are
theArgument = 1556;
let theValue = parseInt(((theArgument % 1000) % 100) % 10);
Expected output: 6

___________________________________________________________________
Describe: convertOnes(theArgument)

test: take in a  number and output that many "I"s using a for loop
Code:
theArgument = 99
ones = howManyOnes(theArgument)
convertedOnes = "";
Expected output "IIIIIIIII"
for(let i = 0; i < ones; i++){ //  reminder i++ = i = i + 1
  convertedOnes = convertedOnes.concat("I");
  }
  return convertedOnes;

text: take in

test: if the number is equal to 9 output "IX"
Code:
theArgument = 9;
Expected output: "IX"

test: (if it is not 9) if the number is greater than or equal to 5 find how much over 5 it is and output "IV" + an "I" for each number over 5
Code:
theArgument = 8;
overFive = theArgument % 5;
Expected output: VIII

test: if the number is equal to 4 output "IV"
Code:
theArgument: 4
Expected output: IV

______________________________________________________________________________________________
Describe: convertTens(theArgument)


test: take in a number and output an "X" for the number in the tens digit using a for loop
Code:
theArgument = 55
tens = howManyTens(theArgument)
Expected output "XXXXX"

test: if the number of tens equal to 9 output "XC"
Code:
theArgument = "90";
Expected output: "XC"

test: (if it is not 9) if the number of tens is greater than or equal to 5 find how much over 5 it is and output "L" + an "X" for each number over 5
Code:
theArgument = 80;
overFive = theArgument % 5;
Expected output: DXXX

test: if the number of tens is equal to 4 output "XL"
Code:
theArgument: 44
Expected output: XL

________________________________________________________________


Describe: convertHundreds(theArgument)


test: take in a number and output a "C" for the number in the hundreds digit using a for loop
Code:
theArgument = 565
tens = howManyTens(theArgument)
Expected output "CCCCC"

test: if the number of hundreds equal to 9 output "CM"
Code:
theArgument = "900";
Expected output: "CM"

test: (if it is not 9) if the number of hundreds is greater than or equal to 5 find how much over 5 it is and output "D" + a "C" for each number over 5
Code:
theArgument = 800;
overFive = theArgument % 5;
Expected output: DCCC

test: if the number of hundreds is equal to 4 output "CD"
Code:
theArgument: 440
Expected output: CD
________________________________________________________________


Describe: convertThousands(theArgument)


test: take in a number and output a "M" for the number in the thousands digit using a for loop
Code:
theArgument = 3456
tens = howManyTens(theArgument)
Expected output "MMMM"

___________________________________________________________________________________________
Describe: convertAll(theArguement)

test: take in a number and see if it is valid. If it is take the number of each digit and store to a variable for each. if a digit is zero return "" else run the approprait conversion on it and add it to a string. 
Code:
theArgument = 3456
ones = convertedOnes(theArgument)
tens = convertedTens(theArgument)
hundreds = convertedHundreds(theArgument)
thousands = convertedThousands(theArgument)
convertedNumber = thousands + hundreds + tens + ones;

Expected output: MMMCDLVI


