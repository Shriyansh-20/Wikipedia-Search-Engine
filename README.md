# Wikipedia-Search-Engine
_________________________________________________________________________________________________________________________________________________________________________________________
## Prerequisites:-

1. Python3
2. nltk
3. etree
4. stop words list

## About Project
Developed a comprehensive search engine by constructing an Inverted Index on the Wikipedia corpus (72 GB), enabling it to deliver top search results for given query words.

Following Steps Follows to create Inverted Indexing :-

* Parsing using etree : Need to parse each page , title tag, infobox, body , category etc..
* Tokenization : Tokenize sentense to get each token using regular expression
* Case Folding : make it all to lowercase
* Stop Words Removal : remove stop word which are more frequently occured in a sentences
* Stemming : get root/base word and store it
* Inverted Index Creation : create word & its positing list consist of doc_id : TF-IDf score

Posting List for title/body/infobox/category file:
```
word1 : doc_id_1 : 70.34, doc_id_30 : 50.12, doc_id_35 : 20
word2 : doc_id_2 : 40.12, doc_id_35 : 20.78
```

Word_dictionary :

```
word1 : { t : title_file_offset , b : body_file_offset, c : category_file_offset, i : inforbox_file_offset}
word2 : { t : title_file_offset , b : body_file_offset, c : category_file_offset, i : inforbox_file_offset}
```

## Features

* support field query like title:abc body:aaa infobox:zyx
* showing only top 10 relevent search result
* Response time is nearly 1-2 second
  
## Challenges

1. Difficult to process such huge Data dump of 73 GB
2. Can not store word & its posting list into a main memory, So Used K-way Merge sort
3. Can not Load full final index into main memory, So Built Secondary Index on top of Primary Index (Posting List)

### To Create indexing from Wiki Dump
```
python3 wiki_indexer.py <wiki_dump_path> <index_path>
```
eg : `
python3 wiki_indexer.py /users/shriyansh/Documents/IRE/projects/mini-projects/wikipedia-search-engine/phase-2/dump_wikipedia.xml /users/shriyansh/Documents/IRE/projects/mini-projects/wikipedia-search-engine/phase-2/index_files
`

### To Search Query

```
python3 search.py <index_path>
```

eg : `
python3 search.py /users/shriyansh/Documents/IRE/projects/mini-projects/wikipedia-search-engine/phase-2/index_files
`


