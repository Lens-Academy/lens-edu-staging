---
id: b2c3d4e5-f6a7-8901-bcde-f23456789012
duration_minutes: 5
tldr: "A demo lens pulling three short excerpts from one Wikipedia article on existential risk from AI, showing how excerpt boundaries, carried-forward source metadata, and collapsed skipped text appear to the reader."
summary_for_tutor: "Demonstrates the article-excerpt feature by drawing three ranges from a single source article (Wikipedia's 'Existential risk from artificial intelligence'), interleaved with text segments and a closing demo chat. It shows how excerpt from/to anchors work, how a later Article segment inherits the earlier source, and how skipped material collapses. The subject text is incidental; the lens exists to illustrate excerpting mechanics."
title: Article excerpt demo
---
#### Text
content::
This lens shows three short excerpts from the same article.

#### Article
source:: [[../articles/wikipedia-existential-risk-from-ai]]
from:: "**Existential risk from artificial intelligence**"
to:: "irreversible [global catastrophe]"

#### Text
content::
The UI can show collapsed content before or after excerpts when the source article has skipped material.

#### Article
%%The processor carries the article source forward, so later `#### Article` segments can omit `source::`. %%
from:: "> The upshot is simply a question of time"
to:: "moment question."

%% You can also add {--{"author":"James agent ready-31's AI","timestamp":1791539502748}@@multiple--}{++{"author":"James agent ready-31's AI","timestamp":1791539502748}@@several++} article excerpts in a {--{"author":"James agent ready-31's AI","timestamp":1791539502748}@@row. --}{++{"author":"James agent ready-31's AI","timestamp":1791539502748}@@row, as long as something is left out between them (here the sentence that introduces Turing's quote, which shows as folded text). Two excerpts with nothing between them are a validator error: merge them into one excerpt instead. ++}%%
#### Article
from:: {--{"author":"James agent ready-31's AI","timestamp":1791539502748}@@"In 1951, foundational computer scientist"
to:: "of--}{++{"author":"James agent ready-31's AI","timestamp":1791539502748}@@"> Let us now assume, for++} the {--{"author":"James agent ready-31's AI","timestamp":1791539502748}@@world as they became more intelligent than human beings:"--}{++{"author":"James agent ready-31's AI","timestamp":1791539502748}@@sake of argument"
to:: "converse with each other to sharpen their wits."++}

#### Chat
instructions::
This is a demo chat after article excerpts. Ask the learner what they noticed about article metadata, excerpt boundaries, and collapsed skipped text.

%%Such chat fields can be placed anywhere, by the way. Also in-between pieces of article and text.%%
