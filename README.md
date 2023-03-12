# UIKit-TicTacToe 🎮

Welcome to the UIKit-TicTacToe repository! This repository contains a classic Tic-Tac-Toe game developed using UIKit framework for iOS. 📱🕹️

## Overview 📝

The UIKit-TicTacToe game allows two players to play the classic Tic-Tac-Toe game on their iOS devices. The game features a clean and modern user interface, sound effects, and animations. 🎨🔊💥

The project includes the following features:

- A modern and user-friendly interface that is easy to use and navigate 📱👀
- Two-player gameplay with support for multiple rounds 🤼‍♂️
- Customizable player names and game settings 🏷️⚙️
- Sound effects and animations that enhance the gameplay experience 🔊💥

## Getting Started 🚀

To get started with the UIKit-TicTacToe game, simply clone this repository and open the Xcode project file. You can then build and run the game in the iOS Simulator or on a physical iOS device. 🛠️📱

## Usage 🤖

To use the UIKit-TicTacToe game in your own iOS app, simply copy the necessary files to your project and modify the code to fit your needs. The project is designed to be modular and customizable, so you can easily add or remove features as needed. 📝🎨

```swift
import UIKit

class TicTacToeViewController: UIViewController {

    // MARK: - Properties
    
    var game: TicTacToeGame!
    var currentPlayerLabel: UILabel!
    var boardView: BoardView!
    var resetButton: UIButton!
    
    // MARK: - View Lifecycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        // Set up the game
        game = TicTacToeGame()
        game.delegate = self
        
        // Set up the UI
        currentPlayerLabel = UILabel()
        boardView = BoardView()
        resetButton = UIButton()
        
        // Add the views to the view hierarchy
        view.addSubview(currentPlayerLabel)
        view.addSubview(boardView)
        view.addSubview(resetButton)
        
        // Layout the views
        // ...
    }
    
    // MARK: - Actions
    
    @objc func resetButtonTapped() {
        game.reset()
    }

}

// MARK: - TicTacToeGameDelegate

extension TicTacToeViewController: TicTacToeGameDelegate {

    func ticTacToeGame(_ game: TicTacToeGame, didUpdateBoard board: [[TicTacToePiece]]) {
        // Update the board view
        boardView.update(with: board)
    }
    
    func ticTacToeGame(_ game: TicTacToeGame, didUpdateCurrentPlayer player: TicTacToePlayer) {
        // Update the current player label
        currentPlayerLabel.text = "\(player.name)'s turn"
    }
    
    func ticTacToeGame(_ game: TicTacToeGame, didEndWithWinner winner: TicTacToePlayer?) {
        // Display the winner (or a tie) in an alert
        let alertController = UIAlertController(title: "Game Over", message: winner == nil ? "It's a tie!" : "\(winner!.name) wins!", preferredStyle: .alert)
        alertController.addAction(UIAlertAction(title: "OK", style: .default, handler: { _ in
            self.game.reset()
        }))
        present(alertController, animated: true, completion: nil)
    }

}
```

Credits 🙌

The UIKit-TicTacToe game was created by Javier Canto as a simple example of how to use UIKit in an iOS app.
