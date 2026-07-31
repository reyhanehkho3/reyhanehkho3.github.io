---
title: Regex
publish: true
date created: 2026-07-30
---
### Regex characters:
#### Meaningful characters:
- `.` can be any character.
- `\` to use the characters themselves and not their regex representation.
- `\d` all numbers.
- `\D` all characters excepts numbers.
- `\w` all English letters, numbers and -.
- `\W` !\w.
#### Counting characters:
- `+` shows that a character is repeated one or more times.
- `*` the previous character is repeated 0 or more times. (like `+` but the repetition is at least 0)
- `?` the previous character is present 0 or 1 time. 
- `{}` certain number of repetition for a char. like `a{3}`: aaa. It can also be an interval. 

### Lookahead
- Positive Lookahead: Checks if after the text there is a certain condition. 
	`something(?=condition)`
- Negative Lookahead: the same as the positive but it check if the condition is not met. 
	`something(?!condition)`