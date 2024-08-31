**Strategy** is a behavioral design pattern that lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.


```python
# AbstractStrategy.py

from typing import List
from abc import ABC, abstractmethod
import random

class SongPlayingStrategy(ABC):
    @abstractmethod
    def select_next_song(self, playlist: List[str], current_song: str) -> str:
        pass
        

# ConcreteStrategy.py

class SequentialPlayStrategy(SongPlayingStrategy):
    def select_next_song(self, playlist: List[str], current_song: str) -> str:
        if current_song is None:
            return playlist[0]
        next_index = (playlist.index(current_song) + 1) % len(playlist)
        return playlist[next_index]

class ShufflePlayStrategy(SongPlayingStrategy):
    def __init__(self):
        self.played_songs: Set[str] = set()

    def select_next_song(self, playlist: List[str], current_song: str) -> str:
        if len(self.played_songs) == len(playlist):
            self.played_songs.clear() # Reset once all songs have been played.
        next_song = current_song
        while next_song in self.played_songs or next_song == current_song:
            next_song = random.choice(playlist)
        self.played_songs.add(next_song)
        return next_song

class RepeatOneStrategy(SongPlayingStrategy):
    def select_next_song(self, playlist: List[str], current_song: str) -> str:
        return current_song

class RepeatAllStrategy(SequentialPlayStrategy):
    pass


# context.py

class MusicPlayer:
    def __init__(self, playlist: List[str]):
        self.playlist = playlist
        self.current_song = None
        self.strategy = SequentialPlayStrategy()

    def set_strategy(self, strategy: SongPlayingStrategy):
        self.strategy = strategy

    def play_next(self):
        self.current_song = self.strategy.select_next_song(self.playlist, self.current_song)
        print(f"Playing: {self.current_song}")

```