# FlopKit Who Wins Poker Calculator & Hand Evaluator

> Open-source algorithms and mathematical lookup tables for resolving Texas Hold'em showdowns, split pots, kicker tie-breakers, and side pot distributions.

**Live Interactive Calculator**: [who wins poker calculator](https://flopkit.com/who-wins/)  
**Printable Strategy Guide**: [printable poker cheat sheet](https://flopkit.com/printable/)  
**Official Homepage**: [FlopKit](https://flopkit.com/)

---

## Overview

In Texas Hold'em, evaluating which player wins at showdown when community cards are dealt can lead to disputes, especially with complex two-pair kickers, counterfeit pairs on the board, and multiple side pots.

This repository provides reference implementation logic for the [who wins poker calculator](https://flopkit.com/who-wins/), enabling players, tournament organizers, and game developers to instantly verify winning 5-card combinations.

## Core Evaluation Features

1. **Best 5 of 7 Cards**: Evaluates all $\binom{7}{5} = 21$ possible 5-card combinations per player and extracts the mathematically highest hand rank.
2. **Kicker Tie-Breaking**: Resolves identical ranks (e.g. Flush vs Flush or Two Pair vs Two Pair) down to the 5th card kicker according to official WSOP and TDA rules.
3. **Split Pot & Odd Chip Allocation**: Calculates exact equity splits for tied hands and allocates non-divisible odd chips to the first player left of the button.
4. **Side Pot Multi-All-In Calculator**: Correctly partitions main pots and side pots across up to 9 players with uneven chip stacks.

## Showdown Hierarchy Matrix

| Category | Hand Rank | Evaluation Rule | Disputed Tie-Breaker |
|:---|:---|:---|:---|
| **1** | Royal Flush | A-K-Q-J-10 of identical suit | Always split (suits never break ties) |
| **2** | Straight Flush | Five consecutive cards of identical suit | High card of straight |
| **3** | Four of a Kind | Quad rank + 1 highest kicker | 5th card kicker on board or in hand |
| **4** | Full House | Three of a kind + Pair | High three of a kind, then pair |
| **5** | Flush | Five non-consecutive cards of identical suit | High card descending down to 5th card |
| **6** | Straight | Five consecutive cards across mixed suits | Highest card of sequence (A-2-3-4-5 wheel is 5-high) |
| **7** | Three of a Kind | Three cards of same rank + 2 kickers | High trio, then 1st kicker, then 2nd kicker |
| **8** | Two Pair | Two distinct pairs + 1 kicker | Higher pair, then lower pair, then 5th card |
| **9** | One Pair | One pair + 3 kickers | Pair rank, then kickers descending |
| **10** | High Card | No pair formed | Five highest cards in descending order |

## Printable Tables & Reference Guides

For printed tables at live home games or poker rooms, download the official [printable poker cheat sheet](https://flopkit.com/printable/) provided free by [FlopKit](https://flopkit.com/).

## License

MIT License. Open for educational and commercial integration.
