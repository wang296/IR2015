---
layout: default
title: Visualizing Zipf's law
---

Let's take the text of [Oliver Twist]({{site.baseurl}}/files/oliver-twist.txt)
and investigate the word distribution.

## Counting Words

```ruby
# count alpha words by splitting on whitespace

counts = {}
for word in File.open(ARGV[0], 'r').read.split(" ")
  word = word.chomp.downcase.gsub(/[^a-z]/, "")
  if not word.empty?
    counts[word] = 0 unless counts.has_key? word
    counts[word] += 1
  end
end

# sort based on frequency and save to file

arr = counts.to_a.sort_by{|k,v| v}
out = File.open("counts.txt", 'w')
for pair in arr.reverse
  out << "#{pair[0]}\t#{pair[1]}\n"
end
```

To run the script, just do

```bash
$ ruby count.rb oliver-twist.txt
```

Note that you can count words in any file you specify. The longer the better!

Look at the first 20 lines of the file after running:

```bash
$ head -n 20 counts.txt
the     9771
and     5425
of      3981
to      3948
a       3785
in      2430
he      2396
his     2356
that    1846
was     1787
it      1722
you     1671
i       1626
with    1617
as      1324
said    1230
had     1224
for     1169
mr      1079
him     1060
```

Look at the last 20 lines of the file:

```bash
$ tail -n 20 counts.txt
donation        1
laughterhere    1
methods 1
addresses       1
convulsedeh     1
lark    1
checks  1
httppglaforgdonate      1
professor       1
originator      1
bother  1
library 1
volunteer       1
edition 1
pg      1
facility        1
httpwwwgutenbergnet     1
includes        1
subscribe       1
newsletter      1
```

## Plotting the Results

We'll plot the output in the file `counts.txt` with
[R](http://www.r-project.org/).

```bash
# Read data from Ruby output and plot normally

counts = read.table('counts.txt')
plot(counts$V2)

# Now plot on a log-log graph

plot(counts$V2, log="xy", main="Word Ranks in 'Oliver Twist'",
                          xlab="Word Freq Rank",
                          ylab="Word Freq")
```

Here's the original plot:

{% figure 1 %}
{% img files/normal.png %}
{% endfigure %}

And now here it is on a log-log scale:

{% figure 2 %}
{% img files/log-log.png %}
{% endfigure %}

