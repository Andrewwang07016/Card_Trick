# Card_Trick
Use logic to manipulate and develop a card trick game.

// Declares and initializes variables
int column = 0, i = 0;
int seeDeck = 0;
int playAgain = 0;
string name;

// Declares a 52 element array of integers to be used as the deck of cards
int deck[52] = { 0 };

// Declares a 7 by 3 array to receive the cards dealt to play the trick
int play[7][3] = { 0 };


// Generate a random seed for the random number generator
srand(time(0));

// Openning message. Asks the player for his/her name
cout << "Hello, I am a really tricky computer program and " << endl
    << "I can even perform a card trick.  Here's how." << endl
    << "To begin the card trick type in your name: ";
cin >> name;

// Capitalize the first letter of the person's name
name = CapitalizedName(name);

do
{
    // Builds the deck
    BuildDeck(deck, 52);

    // Asks if the player wants to see the entire deck. If so, then it prints it out.
    cout << "Ok " + name + ", first things first.  Do you want to see what " << endl
        << "the deck of cards looks like (1-yes/0-no)? ";
    cin >> seeDeck;

    if (seeDeck == 1)
    {
        cout << endl;
        PrintDeck(deck, 52);
    }

    cout << endl << name << " pick a card and remember it..." << endl;

    // Begins the card trick loop
    for (i = 0; i < 3; i++)
    {
        // Begins the trick by calling the function to deal out the first 21 cards
        Deal(deck, play);

        // Includes error checking for entering which column
        do
        {
            // Asks the player to pick a card and identify the column where the card is
            cout << endl << "Which column is your card in (0, 1, or 2)?: ";
            cin >> column;
        } while (column < 0 || column > 2);
        
        // Picks up the cards, by column, with the selected column second
        PickUp(deck, play, column);
    }

    // Displays the top ten cards, and then reveal the secret card
    SecretCard(deck);

    // Asks if the player wants to play again
    cout << name << ", would you like to play again (1-yes/0-no)? ";
    cin >> playAgain;
} while (playAgain == 1);

// Thanks the player for playing, end message
cout << endl << endl << "Thank you for playing the card trick!" << endl;
return 0;
