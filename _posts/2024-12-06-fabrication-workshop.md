---
layout: post
title: Fabrication Workshop
date: 2024-12-06 00:32:13
description: Reflection on visualizing history using a laser cutter
tags: Digital_Humanities
categories:
tabs: true
---

Over the past two weeks, we brainstormed on ways to represent data in the Umpire through a laser cutter.

Given the mass amount of data regarding the Umpire, it is difficult to determine a concise definition and meaning by first glance. Since each entry in our dataset is categorized by topics such as baseball, ESP league, and religion, we analyzed each topic in depth and decided to focus on religion because we were interested in ways that prisoners remained hopeful during times of loneliness and despair. Another reason is that we already know baseball is a recurring theme in the Umpire, so we wanted to bring a new perspective. Thus, our goal was to use a laser cutter to create a physical, tangible representation of religion in the Umpire. The resulting product was a histogram of the frequency of religious words in the Umpire sitting on top of a birds’ eye view of the ESP, the corresponding words for the frequencies were also inscribed onto the histogram.

We met multiple times in the EC and on Zoom to discuss and complete this project, and everyone was able to contribute meaningfully to each session due to the role specifications. One of our initial ideas was to create a word cloud out of the frequencies of religious words mentioned in the Umpire, but the resulting prototyped image ended up being too crowded and not aesthetically appealing, not to mention that it would be vert difficult for the laser cutter to replicate such a vision. By iterating through ideas and prototypes and discussing pros and cons of each, we narrowed our final idea down to having a histogram with each bar engraved with its corresponding word related to religion.

The acrylic material for the histogram had a reflective finish, so we had another idea to print a poem witten in the ESP as the base of the histogram -- a symbol that religious beliefs create a stable foundation for the inmates. However, laser cutting words would again be difficult to achieve, so we ultimately decided to etch a map of the ESP as the base of the histogram to symbolize that the historical information we used emerged from the grounds of the prison.

During the presentation, we asked our viewers to be able to see their face reflected in the histogram on the other side of where the words were engraved so that the color-changing property of our acrylic material reflects the dynamism of faith itself.

As the Digital Asset Manager, I was present in all meetings in order to provide data analysis. For example, I wrote the code for counting the number of religion-related words using regex, and I also generated the word cloud and histogram as shown below:

<div style="display: flex; justify-content: space-between; gap: 20px;">
    <img src="/assets/img/word_cloud.jpg" alt="Word Cloud" style="width: 48%; height: auto;">
    <img src="/assets/img/histogram.jpg" alt="Histogram" style="width: 48%; height: auto;">
</div>

And here is the code that I used to create the graphs above:

```python
import pandas as pd
import re
import nltk
from nltk.corpus import stopwords
from wordcloud import WordCloud
import matplotlib.pyplot as plt
from collections import Counter

nltk.download('stopwords')
data = pd.read_csv('data.csv')
all_text = ' '.join(data['text'].dropna())

words = re.findall(r'\b[a-zA-Z]+\b', all_text.lower())

stop_words = set(stopwords.words('english'))
filtered_words = [word for word in words if word not in stop_words]

religion_pattern = re.compile(r'\b(god|faith|church|bible|prayer|spiritual|religion|holy|worship|christian|muslim|islam|hindu|buddhist|jewish|temple|synagogue|mosque|sacred|divine|belief|ritual|soul|heaven|hell|angel|sin)\b')

religion_words = [word for word in filtered_words if religion_pattern.search(word)]

word_counts = Counter(religion_words)

print("Religion-Related Words and Their Frequencies:")
for word, frequency in word_counts.items():
    print(f"{word}: {frequency}")

wordcloud = WordCloud(width=800, height=400, background_color='white').generate_from_frequencies(word_counts)

plt.figure(figsize=(10, 5))
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis('off')
plt.title("Religion-Related Word Cloud")
plt.show()
```

```python
import matplotlib.pyplot as plt

words = ['Repent', 'Forgive', 'Faith', 'Devotion', 'Remorse', 'God', 'Sin']
frequencies = [12, 42, 153, 18, 12, 130, 60]

plt.figure(figsize=(10, 6))
plt.bar(words, frequencies, color='skyblue')

plt.title('Frequency of Religion-Related Words')
plt.xlabel('Words')
plt.ylabel('Frequency')

plt.show()
```
