import re

#search the existing cell value for a string that matches the following pattern:
#either "directed by" or "directed and produced by" or "director"(with or without a comma)
#followed by one or more words that begin with capital letters (likely to be the director's name)

g = re.search(ur"((directed by)|(directed and produced by)|(director(,)?))((\s[A-Z]([a-z])*)*)", value)

return g.group(6)
