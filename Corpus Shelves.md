{++{"author":"Lauren's AI","timestamp":1785588507634}@@# The corpus as shelves

An interactive map of 3,233 LessWrong and Alignment Forum posts, compressed and
clustered as raw material for the advanced AI-safety course.

**Live page:** http://flowerbox.tail24ae4.ts.net:9720/shelves.html
(on the tailnet; a public host is still needed for people outside it)

## What it is

Every post was read and compressed to a headline, a paragraph, a type label, a
scope note, and a prerequisites note. The posts were then embedded locally
(Qwen3-Embedding-8B) and clustered into 30 topic shelves, each named and graded
core / adjacent / off-topic.

The page has three expansion stages at both levels: a shelf shows its name, then
its description, then its posts; a post shows its headline, then its source and
metadata, then scope and prerequisites.

## How to read the extras

- **Colour** marks the *type* of post — what the author is doing. Twelve types,
  derived by embedding the type labels themselves and clustering them, so
  near-synonyms ("proposes a frame", "proposes a conceptual frame") land
  together. Warm hues are constructive, red is critical, green is empirical,
  blue is formal, purple is conceptual.
- **The bar** on each line is *typicality* — how close that post sits to the
  centre of its shelf. It is **not** a quality score; an atypical post is often
  the interesting one. 58 posts (1.8%) are geometrically closer to a different
  shelf than their own, and say so on hover.
- **The slider** blends typicality with karma, both normalised across the corpus.
- **The dropdown** filters a shelf to one type.
- Each shelf header shows the mean post date and its standard deviation.

## Known limits

- Two shelves, "Reframing alignment" and "Reframing the Alignment Problem", are
  measurably one cluster that k-means split in half (centroid cosine +0.661, 2.8
  standard deviations closer than a typical pair, and both individually weak).
  They should be merged.
- The prerequisites field is the most interesting output and the least verified.
  It came from asking the compressor what a reader must already understand, and
  the best answer was that some posts need you to *have been tempted by the
  mistake they are arguing against* — a prerequisite no bibliography expresses.

Built by Claude (Tace) with Lauren, 2026-08-01.
++}