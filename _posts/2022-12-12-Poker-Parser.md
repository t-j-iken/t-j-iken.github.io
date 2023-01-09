---
layout: post
title: "Current Research: Poker Hand History Lexer/Parser"
categories: misc
---

Professional poker players review their game and actions with the use of _hand histories_. Hand histories thoroughly describe the hand in its entirety, providing all
information and details pertaining to the hand for review. Online poker sites have their own format for hand histories. Modern day HUDs for online play parse hand histories
to extract statistics about certain player tendencies (Does this player play too many hands? How often does this player fold to 3bets? How often does this player in the BU steal
against EP raises?).

**The overall idea:** Can we create a a poker hand history lexer and parser that takes an entire hand history and compresses it down to a readable string?
Inversely, can we create a parser that takes the converted string and produces a thorough and detailed hand history?

**Even deeper:** Can we take our converted HH string and plug it into a poker solver to discover misplays, leaks, -EV, and +EV actions?

## Example Hand History

(Might be confusing if not familiar with poker strategy or table positions! I wish MathJax was enabled)

Let hero (H) be ourselves and villian (V) be our primary opponent.

**Live $2/$5, 8 handed**

H ($1255) with QsJs in the CO. Folds to V ($1655) in the HJ.  
V raises to $15(3BB). H 3bets to $55(11BB). V calls.  
**FLOP ($117): Qd Ac 9d**  
V bets $60. H calls.  
**TURN ($237): 8d**  
V checks. H checks.  
**RIVER ($237): 7c**  
V bets $300. H calls.  
V shows KdTc for king high, H shows pair of Queens.  
H awarded $837.  

## Example Converted String

_H_{1255}>QsJs>CO._Ft_>HJ>_Raises_{3BB}>_Ft H_>_H_>_Raises_{11BB}>HJ>_Calls_>_FLOP_{117(QdAc9d)}...

## Theoretical Output

    Evaluating hand...
    3Bet against HJ > Good > ~1.2EV
    Call on CBET on FLOP > Okay > ~0.6EV
    Check back on TURN > Best > ~3.2EV
    Call on BET on RIVER > Okay > 0.3EV

## Mathematical Modeling

Let _A_ be the set of actions a player can do if there is no bet:  
_A_ = {_fold, check, bet_}  
If there is a bet:  
_A^b_ = {_fold, call, raise_}  

Let _P_ be the current pot and _Eq_ be our hand equity vs. V's (_vrEq_) range equity.

**Preflop**: If no 3bet: _A^b_ = {_fold, call, raise_} -> compare to GTO opening ranges  
If V bets: (_Eq_ > or < _veEq_) --> Generate EV for --> _A^b_ = {_fold, call, raise_}

**Flop**: If no bet: _A_ = {_fold, check, bet_} -> compare to GTO +EV  
If V bets: (_Eq_ > or < _veEq_ on _BOARD_) --> Generate EV or --> _A^b_ = {_fold, call, raise_}...

**Turn and River...**









