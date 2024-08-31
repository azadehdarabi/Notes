**State** is a behavioral design pattern that lets an object alter its behavior when its internal state changes. It appears as if the object changed its class.

Music Player System:

```python
# PlayerState.py

from abc impotrt ABC, abstractmethod

class PlayerState(ABC):
	@abstractmethod
	def play(self, player):
		pass
	
	@abstactmethod
	def pause(self, player):
		pass

	@abstractmethod
	def stop(self, player):
		pass


# ConcreteState.py

class PlayingState(PlayerState):
    def play(self, player):
        print("Already playing!")

    def pause(self, player):
        player.set_state(PausedState())
        print("Paused the music.")

    def stop(self, player):
        player.set_state(StoppedState())
        print("Stopped the music.")

class PausedState(PlayerState):
    def play(self, player):
        player.set_state(PlayingState())
        print("Resumed the music.")

    def pause(self, player):
        print("Already paused!")

    def stop(self, player):
        player.set_state(StoppedState())
        print("Stopped the music.")

class StoppedState(PlayerState):
    def play(self, player):
        player.set_state(PlayingState())
        print("Started playing music.")

    def pause(self, player):
        print("Can't pause when stopped!")

    def stop(self, player):
        print("Already stopped!")

# context.py

class MusicPlayer:
    def __init__(self):
        self.state = StoppedState()

    def set_state(self, state: PlayerState):
        self.state = state

    def play(self):
        self.state.play(self)

    def pause(self):
        self.state.pause(self)

    def stop(self):
        self.state.stop(self)

# main.py
player = MusicPlayer()
player.play()  # "Started playing music."
player.play()  # "Already playing!"
player.pause()  # "Paused the music."
player.pause()  # "Already paused!"
player.stop()  # "Stopped the music."
player.play()  # "Started playing music."


```