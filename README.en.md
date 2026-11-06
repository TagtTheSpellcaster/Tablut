# Tablut

[Versione italiana](README.md)

[![Version](https://img.shields.io/badge/version-1.1-blue)](#versions)
[![License: AGPL v3](https://img.shields.io/badge/license-AGPL--3.0-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-222?logo=github)](#github-pages-deployment)
[![HTML5](https://img.shields.io/badge/HTML5-single%20file-E34F26?logo=html5&logoColor=white)](index.html)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES2020-F7DF1E?logo=javascript&logoColor=black)](index.html)

[Play it here](https://tagtthespellcaster.github.io/Tablut/)

A browser-based version of tablut, the form of hnefatafl described by Linnaeus in Lapland in 1732, for which the most complete set of rules is available. It consists of a single HTML page, with no build process, dependencies, or installation required. It shares the architecture of the Royal Game of Ur, Senet, and Wari: a game engine separated from the interface, animations, synthesized audio, history, and illustrated rules. Tablut contains no random elements.

## Features

- **Rules** reconstructed from Linnaeus's Latin text (9×9 board, 25 pieces, king in the centre, throne, capture between two enemies, capture against an empty throne, special rules for capturing the king, the king wins by reaching any square on the edge, draws). Modern additions (attackers move first, draw rules) and interpretations are listed in the "Rules, Strategy, Notes & Sources" panel.
- **Four selectable rule sets** in the settings (take effect from the next game): *Linnaeus (standard)*, the default; *Corners (Pilarski)*, where the king wins by reaching a corner, the throne and corners are hostile and reserved for the king, with a 100-move limit; *Citadels (Bologna)*, where the four encampments and the throne act as citadels, the king can escape only through edge squares that are neither corners nor encampments, and a player who cannot move loses; *Bannerlord (simplified)*, where the king can be captured by two attackers from any direction. Comparisons between sources and decisions made where the texts are ambiguous are documented in the "Rules, Strategy, Notes & Sources" panel.
- **Opponent**: computer opponent with three difficulty levels (easy, medium, hard; medium is the default), or two players sharing the same screen. You can play as either the attackers or the defenders. The computer uses alpha-beta search with an evaluation function derived from the strategy section of the source text: clear escape routes from the king to the edge (or corner), king mobility, blocking attackers, and material. When playing as the defenders at medium and hard difficulty, under the Linnaeus and Bannerlord rule sets, it uses the evaluation function described by Pilarski, which performed better in testing.
- **Board**: wooden board with interlaced borders and Norse-inspired knotwork, burnt starting squares, a central throne, pieces decorated with an engraved quatrefoil pattern, and a king bearing a golden rune. All decorations are drawn in code rather than copied from images.
- **Gameplay aids**: possible destinations highlighted (can be disabled), the king's clear escape routes displayed (can be disabled), move suggestions, undo, and draw offers (the computer accepts only if it considers its own position worse).
- **Audio** synthesized with Web Audio: sound effects (enabled by default) and a Norse-inspired soundtrack (disabled by default), featuring a drone, frame drum, bowed lyre, throat singing, and horn, in D Dorian at 66 BPM. The setting is saved in the browser.
- **Illustrated rules**: 15 animated steps, from the board layout to strategy.
- **Tutorial: guided game**: the computer plays against itself, but the game advances only when prompted by the user (the "Next Move" button or right arrow; "Previous Move" or left arrow to go back). A speech bubble on the board explains the reasoning behind each move: captures, threats, blocked or open escape routes for the king, cordons, sacrifices, and losing alternatives whenever the search algorithm identifies them. The game is divided into phases (opening, middlegame, endgame). The *Lessons* tab contains 15 specific situations (openings, middlegames, endgames, covering different rule sets), each verified by the engine when the lesson is opened and reproduced with the same explanatory speech bubbles.
- **Strategy verification**: strategies described in the sources have been tested using the engine; test figures and limitations are documented in the "Rules, Strategy, Notes & Sources" panel.
- **History**: a sequence presented as cinematic title cards, based on the supplied text (Lapland, Linnaeus, the 1811 translation, variants, rediscovery of the Latin original). The mobile device screen stays on during the presentation.
- **Language**: interface available in Italian and English, with an IT/EN selector on the page. Italian is the default language; the selection is saved in the browser.
- Automatic light and dark themes, responsive layout for small screens. Animations are disabled when the operating system's "Reduce Motion" setting is enabled.

## Rules at a Glance

The attackers (16) move first; the defenders have 8 pieces and the king. Pieces move like rooks, without jumping over or stopping on other pieces. No piece may stop on the central throne (it may pass through it if it is empty). A piece is captured when two enemies trap it on opposite sides, or between an enemy and the empty throne; the king counts as a defender for this purpose. The king is captured by four attackers when on the throne, by three when adjacent to the throne, and by two on opposite sides elsewhere. The king wins by reaching any square on the edge of the board. A draw occurs through position repetition, inability to move, or agreement.

## Interpretations and Limitations

- **Passing through the throne**: the text prohibits stopping on the throne; the code allows pieces to pass through it when empty. This is an interpretation of rules 5 and 4, not an explicit statement in the original text.
- **Repetition**: the game is drawn when the same position, with the same player to move, occurs for the second time. This is an implementation choice.
- **Draw by agreement against the computer**: accepted only if the computer's static evaluation is worse than that of the initial position by more than a fixed threshold. This is a heuristic criterion.
- **Computer opponent**: hard difficulty is limited to approximately 1.1 seconds per move (measured in Node: approximately 0.5 s average, 1.05 s maximum), so it is not a perfect player. The relative strength of the difficulty levels was tested through simulated games with limited node counts and a maximum of 200 plies per game, alternating the starting side: medium vs. easy: 44 wins, 0 losses, 6 unfinished games out of 50; hard vs. easy: 19-0-1 out of 20; hard vs. medium: 30-5-5 out of 40. These figures are not an absolute measure of playing strength.
- **Audio**: sounds are generated procedurally and have not been listened to by the code's author; the musical result is left to the listener's judgement. The reference to the style of *Vikings* concerns the intended timbres and atmosphere (drone, frame drum, bowed lyre, singing), not a reproduction of existing tracks.

The engine has been tested with 500 complete random games (invariants: 25 initial pieces, no non-king piece on the throne, piece capture counts) and 47 rule scenarios (movement, capture, the king as a capturing partner, empty throne, king capture in all three cases, rule 11, victory, draw).

## Getting Started

Open `index.html` in a modern browser. The page loads fonts from Google Fonts if the service is reachable; otherwise, it uses system fonts.

## Versions

| Version | Contents |
|---|---|
| 1.0 | Initial release: complete game with three difficulty levels, animations, audio, history, and illustrated rules, available in Italian and English with a language selector. |
| 1.1 | New rule sets (Corners, Citadels, Bannerlord), guided computer-vs-computer tutorial with explanations, specific game situations, and strategy verification. |

## Sources

- Historical background, rules, and tablut strategy text supplied by the project author; the rules are based on Carl Linnaeus's 1732 description in Latin.
- Board reference images supplied by the project author.
- S. Pilarski, *Designing an Effective Tablut Artificial Intelligence*, McGill University (rules with corner victory; heuristic evaluation).
- A. De Filippo, A. Galassi, A. Soriani, G. Trisolini, F. Baldo, F. Chesani, P. Mello, M. Milano (2025), *Improving the Teaching of Artificial Intelligence Through Project-Based Learning on a Board Game*, Intelligenza Artificiale 19(1), 17–29, doi:10.1177/17248035241297789 (citadel rules).
- Jubal, *The Tablut Grandmaster's Guide (Bannerlord)*, Exilian forum, 31 May 2020, <https://exilian.co.uk/forum/index.php?topic=6188.0> (guide to a video game; non-academic source).

## License

Copyright © 2026 Alessandro Valli.

This program is free software: you can redistribute and modify it under the terms of the GNU Affero General Public License, version 3 or later. If you provide a modified version as a network service, you must make its source code available to users. The program is distributed without any warranty. Full license text: [LICENSE](LICENSE) and <https://www.gnu.org/licenses/agpl-3.0.html>.
