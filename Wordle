/*
 * File: Wordle.java
 * -----------------
 * This module is the starter file for the Wordle assignment.
 * BE SURE TO UPDATE THIS COMMENT WHEN YOU COMPLETE THE CODE.
 */

import edu.willamette.cs1.wordle.WordleDictionary;
import edu.willamette.cs1.wordle.WordleGWindow;



public class Wordle extends WordleGWindow {
	
	 String[] dict = WordleDictionary.FIVE_LETTER_WORDS;	
     String randWord = dict[(int) (Math.random() * (dict.length - 1))].toUpperCase();

	 
    public void run() {
        gw = new WordleGWindow();
        gw.addEnterListener((s) -> enterAction(s));
    }

/*
 * Called when the user hits the RETURN key or clicks the ENTER button,
 * passing in the string of characters on the current row.
 */


 public void enterAction(String s) { 
    	int row = gw.getCurrentRow();
    	int x = 0;
    	
    	//Mutated word used for keeping track of which letter's have been checked
    	String mutateW = randWord;
    	
    	//Determines if the word is in the dictionary
    	while(!s.equals(dict[x].toUpperCase()) && x < dict.length - 1)
    	{
    		x++;
    	}
    	
    	/* if the word is in the dictionary...
    	1. Check if the word is equal to randWord, if so done. 
    	
    	for every char in word...
    	
    	2. Check if the i char is equal to the i char of mutateWord. If so, set square + key to correct color. 
    	3. Check if the i char is in MutateWord...
    		3a)If there are numerous i char's in guess: If one of them is in the correct position, mark the rest as missing and continue. 
    		3b)Else, set as present color. 
    	4. Else, set to missing color. 
    	*/
    	
    	if(x < dict.length - 1 || s.equals(dict[dict.length - 1].toUpperCase()))
    	{
    		if(s.equals(randWord))
			{
				for(int col = 0; col < 5; col++)
				{
					gw.setSquareColor(row, col, CORRECT_COLOR);
				}
				gw.showMessage("Nice! You took " + (row + 1) + " tries");
			}
    	
    		
    		for(int i = 0; i < 5; i++)
    		{
    			if(mutateW.charAt(i) == s.charAt(i))
    			{	
    				gw.setSquareColor(row ,i, CORRECT_COLOR);
    				gw.setKeyColor(s.charAt(i) + "", CORRECT_COLOR);
    			}
    			
    			else if (mutateW.contains(s.charAt(i) + ""))
    			{	
    				//MutateGuess is used to determine if the guess has numerous of the given character
    				String mutateGuess = s;
    				mutateGuess = mutateGuess.substring(0, mutateGuess.indexOf(s.charAt(i))) + "1" + mutateGuess.substring(mutateGuess.indexOf(s.charAt(i)) + 1);
    				
    				//Used to prevent being marked as PRESENT when guess has multiple of the same characters and one of them is in the correct position
    				if((mutateGuess.indexOf(s.charAt(i)) == mutateGuess.indexOf(s.charAt(i))) && mutateGuess.indexOf(s.charAt(i)) > -1)
    				{
    					gw.setSquareColor(row, i, MISSING_COLOR);
    					continue;
    				}
    				else 
    				{	
    				mutateW = mutateW.substring(0, mutateW.indexOf(s.charAt(i))) + "1" + mutateW.substring(mutateW.indexOf(s.charAt(i)) + 1);
    				gw.setSquareColor(row, i, PRESENT_COLOR);
    				gw.setKeyColor(s.charAt(i) + "", PRESENT_COLOR);
    				}
    			}
    			else
    			{
    				gw.setSquareColor(row, i, MISSING_COLOR);
    				gw.setKeyColor(s.charAt(i) + "", MISSING_COLOR);
    			}			
    		}	
    		if (s.equals(randWord) && row == 5)
    		{
    			for(int col = 0; col < 5; col++)
    			{
    				gw.setSquareColor(5, col, CORRECT_COLOR);
    			}
    			gw.showMessage("Nice! You took " + (row + 1) + " tries");
    			
    		}
    		else if(row == 5) 
    		{
    			gw.showMessage("The correct word was " + randWord);
    		} 
    		else
    		{
    		 gw.setCurrentRow(++row);
    		}
    	}	
    	else 
    	{
    		gw.showMessage("Not in word list");
    	}
 }
 
 


/* Startup code */

    public static void main(String[] args) {
        new Wordle().run();
    }

/* Private instance variables */

    private WordleGWindow gw;

}
