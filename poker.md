# Blackjack

## Summary

Go Fish! was cool, but it's time to build some more complicated card games! There are two options here: [Blackjack](blackjack.md) or [Poker](poker.md). You can pick whichever game you'd like to implement.

## Requirements

1. Create a repository called `blackjack`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Add, commit, and push your code to your `blackjack` repository.
4. Create a short video \(between 3 and 5 minutes\) demonstrating your game.

## Rules

If you've never played before, it might be worthwhile to watch a video or two on the rules and objectives of the game.

### Ranks

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

That's 13 possible ranks.

### Suits

Each playing card is also assigned one of four suits.

* `Clubs`
* `Diamonds`
* `Hearts`
* `Spades`

If you're keeping track, that gives us 52 possible cards \(i.e., 13 x 4\).

### Values

The suit doesn't matter in Blackjack, but the rank matters very much. Each card is given a numeric value.

* An `Ace` is worth either 1 point or 11 points, whichever is more beneficial to the player.
* A face card \(a `Jack`, `Queen`, or `King`\) is worth 10 points.
* Every other card is worth its rank \(e.g., a `Four` is worth 4 points\).

### Objective

The objective of the game is the get as close to 21 points without going over.

### Wagers

Players must buy-in for certain number of chips. There is not dollar amount associated with a chip, and there's not limit \(aside from memory constraints\) to how many chips a player can buy-in for or possess.

At the beginning of each hand, a player must decide how many chips they'd like to wager. Player's must wager at least 1 chip, but no more than 25 chips.

### Gameplay

There will be one dealer \(computer\) and one player \(human\). Initially, each is dealt two cards \(face down, face up for the dealer; both face up for the player\).

The player goes first. They are allowed to either hit or stand. When a player hits, they are asking for another card from the deck. The idea is to get closer to 21, but they also risk going over. When a player stands, they are accepting their hand and ending their turn.

Next, it's the dealer's turn, at which point the initially face-down card should be turned face-up. The computer must abide by the following rules.

* If the initial hand is 17 or more, the computer must stand.
* if the initial hand is 16 or less, the computer must hit.
* The computer must continue hitting until their hand is 17 or more.

### Winning

If a player is initially dealt exactly 21 \(e.g., an Ace and a King\) on their first two cards, this is called blackjack. The hand is over and the player automatically wins. They payout for this type of win is 3-to-2, meaning 3 chips paid for every 2 chips wagered.

If, after a series of hits and stands, the player's hand is greater than the dealer's \(without exceeding 21\), the player wins and is paid out 1-to-1. This means 1 chip paid for every 1 chip wagered. A tie is called a push, and the player gets their wager back.

If the dealer's hand is greater than the player's hand \(without exceeding 21 of course\) or the player's hand exceeds 21, the player loses the hand and their wagered chips.

## Deliverables

1. Submit your repository URL.
2. Submit a video demo of your game \(between 3 and 5 minutes\).

Your video demo must show the entirety of gameplay \(at least 5 consecutive hands\), including wagering, hitting, standing, and winning or losing.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, December 20, 2020.

