# Go Fish

## Summary

We've worked on a number of problem sets, which have provided you with plenty of opportunities to practice and hone your skills. Now, we're going to work on a something a little more tangible. Together, we're going to write a simple adaptation of a classic card game: Go Fish!

Follow along with the tutorial and get all of the basic functionality in place. Later, you'll have a chance to add your own flair to the game!

## Rules

Before we dive into the code, we need to make sure we have a firm understanding of the objectives and rules of the game. Each player is initially dealt seven cards. The goal is to collect as many books as possible. The player with the most books at the end of the game wins.

### Ranks and Suits

Playing cards have two primary attributes: ranks and suits. A rank is the numeric or face value of a card.

* `Two`
* `Three`
* `Four`
* `Five`
* `Six`
* `Seven`
* `Eight`
* `Nine`
* `Ten`
* `Jack`
* `Queen`
* `King`
* `Ace`

Each playing card is also assigned one of four suits.

* `Clubs`
* `Diamonds`
* `Hearts`
* `Spades`

If you're keeping track, that gives us 52 possible cards.

### Books

A book, within the context of the game, is a collection of all four suits of a single rank. For example, collection the four Aces that exist in the deck.

* `Ace of Clubs`
* `Ace of Diamonds`
* `Ace of Hearts`
* `Ace of Spades`

### Gameplay

Players take turns requesting cards one at a time from each other. If the opposing player possesses the requested card, it must be relinquished to the requester. Otherwise, the requester must draw a single card from the deck.

Whenever a book is completed, it must be made visible to both players. If, in the event a player has no cards remaining \(but there are cards remaining in the deck\), the player draws a single card before taking their turn. The game ends when all 13 books are completed. Whoever has the most books is the winner.

## Design

The design of the application is pretty simple. We'll be working with cards, of course, and players who will be holding sets of these cards.

* `Card`
* `Player`

A third entity will be used to manage the player and computer interactions.

* `GoFish`

Each of these classes will have very specific responsibilities.

### Card

The `Card` class is primarily responsible for keeping track of its rank and suit, as well as providing means to print itself.

{% code title="Card.java" %}
```java
public class Card {

    private String rank;
    private String suit;

    public Card(String rank, String suit) {
        this.rank = rank;
        this.suit = suit;
    }

    public String getRank() {
        return rank;
    }

    public String getSuit() {
        return suit;
    }

    @Override
    public String toString() {
        return rank + suit;     // allows for easy printing of a card
    }
}
```
{% endcode %}

There are a few other `Card`-related functions we'll want in place. Sorting, for starters, is something we'll want and a couple methods in the class can simplify that process.

These should go right below the `toString` method.

```java
public static int getOrderedRank(String rank) {
    try {
        return Integer.parseInt(rank);
    } catch (NumberFormatException e) {
        switch (rank) {
            case "T": return 10;    // for 10s, Jacks, Queens, Kings,
            case "J": return 11;    // and Aces, we need to apply a
            case "Q": return 12;    // numeric value to simplify the
            case "K": return 13;    // sorting of hands and books.
            case "A": return 14;
        }
    }

    return -1;
}

public static int getOrderedSuit(String suit) {
    switch (suit) {
        case "C": return 1;     // we give each suit a numeric
        case "D": return 2;     // value to simplify the sorting
        case "H": return 3;     // of hands.
        case "S": return 4;
    }

    return -1;
}
```

And lastly, we'll want a means by which we can convert a requested rank to a `Card` object. This should go underneath the `getOrderedSuit` method.

```java
public static Card getCardByRank(String rank) {
    if (rank == null) return null;
    if (rank.length() != 1) return null;

    // return a card based on a rank, returning null if the provided
    // rank is invalid or unrecognized

    if (rank.equals("T") ||
        rank.equals("J") ||
        rank.equals("Q") ||
        rank.equals("K") ||
        rank.equals("A"))
    {
        return new Card(rank, null);
    } else {
        try {
            int number = Integer.parseInt(rank);

            if (number > 1 && number < 10) {
                return new Card(rank, null);
            }
        } catch (NumberFormatException e) {
            return null;    // this happens if rank isn't a number
        }
    }

    return null;
}
```

### Player

The `Player` class has bit more complexity. It keeps track of two lists of `Card`s, one for the hand and another for completed books.

{% code title="Player.java" %}
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

public class Player {

    private final List<Card> hand;
    private final List<String> books;

    public Player() {
        this.hand = new ArrayList<>();
        this.books = new ArrayList<>();
    }

    public List<Card> getHand() {
        return hand;
    }

    public List<String> getBooks() {
        return books;
    }
}
```
{% endcode %}

Now for the complexity I mentioned. Let's start slow. `Player`s need the ability to take a `Card` \(or, in some contexts, be given a `Card`\), as well as relinquish a `Card`. The game, itself, needs to be able to determine if a `Player` has a `Card` in their hand.

We'll put each of these underneath the `getBooks` method.

```java
public void takeCard(Card card) {
    hand.add(card);
    sortHand();
}

public boolean hasCard(Card card) {
    for (Card c : hand) {
        if (c.getRank().equals(card.getRank())) {
            return true;    // yes, they have the card
        }
    }

    return false;   // no, they don't
}

public void relinquishCard(Player player, Card card) {
    int index = findCard(card);

    if (index != -1) {
        Card c = hand.remove(index);    // remove the card from this player
        player.getHand().add(c);        // add the card to another player

        sortHand();
        player.sortHand();
    }
}
```

There are several references to methods that haven't yet been implemented. Don't worry, we'll get to those shortly. Ready to pick up the pace? As we collect `Card`s, we need to remove books from our hand and put them in a separate list \(i.e., the equivalent of showing these cards on the table\).

```java
public boolean findAndRemoveBooks() {
    for (int i = 0; i < hand.size() - 1; i++) {
        int frequency = 1;

        for (int j = i + 1; j < hand.size(); j++) {
            if (hand.get(i).getRank().equals(hand.get(j).getRank())) {  // tallies cards of the same rank
                frequency++;
            }
        }

        if (frequency == 4) {   // if we have all 4 cards, transfer them to the books list
            return removeSets(i);
        }
    }

    return false;
}
```

This next method is similar to `findAndRemoveBooks`. Rather than removing books, though, it's searching for the most frequently occurring `Card` in the hand. This is how the computer determines the `Card` to request from the `Player`.

```java
public Card getCardByNeed() {
    int index = 0;
    int frequency = 1;

    for (int i = 0; i < hand.size() - 1; i++) {
        int count = 1;

        for (int j = i + 1; j < hand.size(); j++) {
            if (hand.get(i).getRank().equals(hand.get(j).getRank())) {  // tallies cards of the same rank
                count++;
            }
        }

        if (count > frequency) {    // updates which card is the most frequently occurring
            index = i;
            frequency = count;
        }
    }

    return hand.get(index);
}
```

We've referenced several methods that aren't yet in existence.

* `findCard`
* `removeSets`
* `sortHand`
* `sortBooks`

Time to implement those methods! Put these below `getCardByNeed`.

```java
private int findCard(Card card) {
    for (int i = 0; i < hand.size(); i++) {
        if (hand.get(i).getRank().equals(card.getRank())) {     // find card by rank
            return i;
        }
    }

    return -1;
}

private boolean removeSets(int index) {
    books.add(hand.get(index).getRank());   // add rank to books

    for (int i = 0; i < 4; i++) {
        hand.remove(index);     // remove all 4 cards
    }

    sortHand();
    sortBooks();

    return true;
}

private void sortHand() {
    hand.sort((a, b) -> {
        if (Card.getOrderedRank(a.getRank()) == Card.getOrderedRank(b.getRank())) {
            return Card.getOrderedSuit(a.getSuit()) - Card.getOrderedSuit(b.getSuit());     // order by suit if
        }                                                                                   // ranks are the same

        return Card.getOrderedRank(a.getRank()) - Card.getOrderedRank(b.getRank());         // otherwise, by rank
    });
}

private void sortBooks() {
    books.sort(Comparator.comparingInt(Card::getOrderedRank));  // sort books by rank using return
}
```

There's some tricky syntax here, so let's review it. The arrow \(`->`\) is called a lambda function. It's a shorthand syntax for passing a function into the sort method. When sorting the list, every pair of values is passed into the lambda function, where they are sorted by rank and suit.

The double colon \(`::`\) is a method reference operator. In this case, it means every value of the list is passed to the `getOrderedRank` method, and the return value is used to sort.

### GoFish

The `GoFish` class manages the user \(and computer!\) interactions of the application.

{% code title="GoFish.java" %}
```java
import java.util.*;

public class GoFish {

    private final String[] SUITS = { "C", "D", "H", "S" };
    private final String[] RANKS = { "A", "2", "3", "4", "5", "6", "7", "8", "9", "T", "J", "Q", "K" };

    private char whoseTurn;
    private final Player player;
    private final Player computer;
    private List<Card> deck;
    private final Scanner in;

    public GoFish() {
        this.whoseTurn = 'P';
        this.player = new Player();
        this.computer = new Player();
        this.in = new Scanner(System.in);
    }

    public void play() {
        shuffleAndDeal();

        // play the game until someone wins

        while (true) {
            if (whoseTurn == 'P') {
                whoseTurn = takeTurn(false);

                if (player.findAndRemoveBooks()) {
                    System.out.println("PLAYER: Oh, that's a book!");
                    showBooks(false);
                }
            } else if (whoseTurn == 'C') {
                whoseTurn = takeTurn(true);

                if (computer.findAndRemoveBooks()) {
                    System.out.println("CPU: Oh, that's a book!");
                    showBooks(true);
                }
            }

            // the games doesn't end until all 13 books are completed. the player with the
            // most books at the end of the game wins.

            if (player.getBooks().size() + computer.getBooks().size() == 13) {
                if (player.getBooks().size() > computer.getBooks().size()) {
                    System.out.println("\nCongratulations, you win!");
                } else {
                    System.out.println("\nOh, better luck next time. This game goes to the computer...");
                }
                break;
            }
        }
    }

    public void shuffleAndDeal() {
        if (deck == null) {
            initializeDeck();
        }
        Collections.shuffle(deck);  // shuffles the deck

        while (player.getHand().size() < 7) {
            player.takeCard(deck.remove(0));    // deal 7 cards to the
            computer.takeCard(deck.remove(0));  // player and the computer
        }
    }

    ////////// PRIVATE METHODS /////////////////////////////////////////////////////

    private void initializeDeck() {
        deck = new ArrayList<>(52);

        for (String suit : SUITS) {
            for (String rank : RANKS) {
                deck.add(new Card(rank, suit));     // adds 52 cards to the deck (13 ranks, 4 suits)
            }
        }
    }

    private char takeTurn(boolean cpu) {
        showHand(cpu);
        showBooks(cpu);

        // if requestCard returns null, then the hand was empty and new card was drawn.
        // this restarts the turn, ensuring the updated hand is printed to the console.

        Card card = requestCard(cpu);
        if (card == null) {
            return cpu ? 'C' : 'P';     // restart this turn with updated hand
        }

        // check if your opponent has the card you requested. it will be automatically
        // relinquished if you do. otherwise, draw from the deck. return the character
        // code for whose turn it should be next.

        if (!cpu) {
            if (computer.hasCard(card)) {
                System.out.println("CPU: Yup, here you go!");
                computer.relinquishCard(player, card);

                return 'P';
            } else {
                System.out.println("CPU: Nope, go fish!");
                player.takeCard(deck.remove(0));

                return 'C';
            }
        } else {
            if (player.hasCard(card)) {
                System.out.println("CPU: Oh, you do? Well, hand it over!");
                player.relinquishCard(computer, card);

                return 'C';
            } else {
                System.out.println("CPU: Ah, I guess I'll go fish...");
                computer.takeCard(deck.remove(0));


                return 'P';
            }
        }
    }

    private Card requestCard(boolean cpu) {
        Card card = null;

        // request a card from your opponent, ensuring that the request is valid.
        // if your hand is empty, we return null to signal the calling method to
        // restart the turn. otherwise, we return the requested card.

        while (card == null) {
            if (!cpu) {
                if (player.getHand().size() == 0) {
                    player.takeCard(deck.remove(0));

                    return null;
                } else {
                    System.out.print("PLAYER: Got any... ");
                    String rank = in.nextLine().trim().toUpperCase();
                    card = Card.getCardByRank(rank);
                }
            } else {
                if (computer.getHand().size() == 0) {
                    computer.takeCard(deck.remove(0));

                    return null;
                } else {
                    card = computer.getCardByNeed();
                    System.out.println("CPU: Got any... " + card.getRank());
                }
            }
        }

        return card;
    }

    private void showHand(boolean cpu) {
        if (!cpu) {
            System.out.println("\nPLAYER hand: " + player.getHand());   // only show player's hand
        }
    }

    private void showBooks(boolean cpu) {
        if (!cpu) {
            System.out.println("PLAYER books: " + player.getBooks());   // shows the player's books
        } else {
            System.out.println("\nCPU books: " + computer.getBooks());  // shows the computer's books
        }
    }

    ////////// MAIN METHOD /////////////////////////////////////////////////////////

    public static void main(String[] args) {
        System.out.println("#########################################################");
        System.out.println("#                                                       #");
        System.out.println("#   ####### #######   ####### ####### ####### #     #   #");
        System.out.println("#   #       #     #   #          #    #       #     #   #");
        System.out.println("#   #  #### #     #   #####      #    ####### #######   #");
        System.out.println("#   #     # #     #   #          #          # #     #   #");
        System.out.println("#   ####### #######   #       ####### ####### #     #   #");
        System.out.println("#                                                       #");
        System.out.println("#   A human v. CPU rendition of the classic card game   #");
        System.out.println("#   Go Fish. Play the game, read and modify the code,   #");
        System.out.println("#   and make it your own!                               #");
        System.out.println("#                                                       #");
        System.out.println("#########################################################");

        new GoFish().play();
    }
}
```
{% endcode %}

## Enhancements

After completing the tutorial, you'll be tasked with making a couple enhancements to this application.

### Multiplayer

As it stands, the game is designed to work with one human player and one computer player. Refactor the code so that the user has the option to play against the computer or another human opponent.

### Smarter

The computer isn't a very good player. It keeps requesting the same `Card` over and over \(the most frequently occurring one\), even if there are other `Card`s that occur with the same or close to the same frequency. Improve the computer's skill by instructing it to make smarter, more human-like decisions.

## Deliverables

1. Submit your repository URL.

Your program output should match the tutorial exactly, plus the enhancements you've made.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, November 22, 2020.

