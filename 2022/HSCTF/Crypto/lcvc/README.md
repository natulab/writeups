# [Crypto] lcvc
### 問題内容
シーザー暗号のちょっと手の混んだ問題

シフトする数(state)が文字ごとに毎回計算されているので
復号するときは同じ分だけ戻してあげればフラグが出る。

flag{iguessthisiswhatyouwouldcallalinearcongruentialvigenerecipher}

```python
#!/usr/bin/env python3

# importS
from string import ascii_lowercase

# main
if __name__ == '__main__':

    state = 1
    ciphertext = 'mawhxyovhiiupukqnzdekudetmjmefkqjgmqndgtnrxqxludegwovdcdmjjhw'
    alphabet = ascii_lowercase

    plaintext = ''
    for c in ciphertext:
        state = (15 * state + 18) % 29
        index = alphabet.index(c) - state
        if index < 0:
            index = index + 26
        plaintext = plaintext + alphabet[index]
    
    flag = 'flag{' + plaintext + '}'
    print(flag)

```
