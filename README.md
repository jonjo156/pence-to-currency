# pence-to-currency

void main() {
	
	 // Below you have an integer of 123456
	 int costInPence = 1234563252542;
	 // This is the total cost of a product in pence.
	  
	  // Your challenge is to create a function to convert this integer to pounds.
	 // The number should end up looking like this: £1,234.56
	 // Notice there are commas to separate the thousands, a decimal place and a currency symbol.
	  
	  // Your code should work for any number that is put into the function, e.g 123456789
  
  convertPenceToPounds(costInPence);
    

  
	}

// 1. Convert it to string
// 2. Put a decimal 2 places in
// 3. Reverse the string
// 4. every three characters, put in a comma
// 5. Add a '£' at the start

// another was is create a list of numbers

  void convertPenceToPounds(int pence) {
    // Convert pence from int to string
    String penceAsString = pence.toString();
    // get last two characters of the string and save them as a variable. These will be the decimal places
    String decimalPlaces = penceAsString.substring(penceAsString.length - 2);
    // get the rest of the characters as these will be the pounds
    String pounds = penceAsString.substring(0, penceAsString.length - 2);
    // perform the function to add commas on pounds
    var newPounds = addCommas(pounds);
    
    print('£' + newPounds + '.' + decimalPlaces);
  }


  String addCommas(String pounds){
    // reverse the string so we can add a comma each 3 characters
    String reversePounds =  pounds.split('').reversed.join('');
    
    //create an empty String to be added to during the loop
    List<String> commaPoundsList = [];
    
    //loop through the new String
    for (int i=0; i<reversePounds.length; i++){
      if (i % 3 == 0 && i != 0) {
        //if it is the third character and not 0, add a comma and then the number
        commaPoundsList.add(',' + reversePounds.substring(i, i+1));
      } else {
        // else, just add the number
        commaPoundsList.add(reversePounds.substring(i, i+1));
      }
    }
    
    //join all the strings together, and then reverse them back to their original order
    return commaPoundsList.join().split('').reversed.join('');
    
  }
