# Python数据模型

Python 解释器碰到特殊的句法时，会使用特殊方法去激活一些基本的对 象操作，这些特殊方法的名字以两个下划线开头，以两个下划线结尾（例如 __getitem__）。 比如 obj[key] 的背后就是 __getitem__ 方法，为了能求得 my_collection[key] 的值，解释器实际上会调用 my_collection.__getitem__(key)。



## 一摞Python风格的纸牌

```python
import collections

Card = collections.namedtuple('Card', ['rank', 'suit'])


class FrenchDeck:
    ranks = [str(n) for n in range(2, 11)] + list('JQKA')
    suits = 'spades diamonds clubs hearts'.split()

    def __init__(self):
        self._cards = [Card(rank, suit)
                       for suit in self.suits for rank in self.ranks]

    def __len__(self):
        return len(self._cards)

    def __getitem__(self, position):
        return self._cards[position]
```


