---
layout: post
title:      "Permitting params in Rails"
date:       2021-02-03 19:14:46 -0500
permalink:  permitting_params_in_rails
---

I recently remembered about a time when I was building a Rails app for a project for Flatiron School and I was so stuck....

I was trying to use a drop down menu to select an existing language or create one manually when entering a new vocab to my VocabBank. Here is a screen shot of my app so you can follow what I am explaining a little better:

![img](https://i.imgur.com/l2sYDkO.png[/img]http://)

When selecting a language from the list, everything worked fine, but when creating a new one, that's when the problems started. I could not, for the life of me, figure out how to get the language_id of the vocab to get passed into vocabs#create. I was requiring language_id in my strong params and I had ```accepts_nested_attributes_for :language``` in my Vocab model, so I was confused about why it was not working. It turns out I was missing something...

I didn't add language_attributes to my strong params. Because the language was nested in my vocab form, I needed to specify which nested attributes were permitted. 

So instead of this:

```
def vocab_params 
    params.require(:vocab).permit(:word_or_phrase, :translation, :user_id, :language_id)
end
```
		 
I needed this:

```
def vocab_params 
    params.require(:vocab).permit(:word_or_phrase, :translation, :user_id, :language_id, language_attributes:      [:language_name])
     
end
```
		 
I also needed to permit :language_name under those language_attributes.


Strong params is a way to protect the database from receiving bad data. 


