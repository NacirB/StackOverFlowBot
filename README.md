## Description

This repository contains a dialogue chat bot, which is able to:

* answer programming-related questions (using StackOverflow dataset);
* chit-chat and simulate dialogue on all non programming-related questions.

For a chit-chat mode we will use a pre-trained neural network engine available from  [ChatterBot](https://github.com/gunthercox/ChatterBot).
For the programming-related questions mode we will train a classifier that will predict exactly one tag (=programming language) and will be also based on Logistic Regression with TF-IDF features. Then we rank questions using embeddings to calculate similarity between the question and existing threads (question on StackOverflow).

## Installation

- Run the week5-project.ipynb to generate train models.
- Run the main_bot.py by passing the token of your telegram bot as an argument. See doc [here](https://core.telegram.org/bots#creating-a-new-bot). to learn how to create a telegram bot.

```bash
python install main_bot.py --token "your_token_here"
```

## Troubleshooting

### Bot crashes with the unicode error 

If your bot code crashes with the error that ends with `UnicodeEncodeError: 'ascii' codec can't encode character`,
your terminal likely has problems showing unicode symbols. To fix this you can change your terminal local by adding
the following lines to you `~/.bashrc` file (or any other shell configuration):

```
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8
```

To verify the effect, you can run the following command end check that it outputs 'utf-8'
```python
> python -c 'import locale; print(locale.getpreferredencoding())'
utf-8
```

You can find more details in this [article](https://perlgeek.de/en/article/set-up-a-clean-utf8-environment).

If this doesn't work, you can explicitly specify the encoding when opening files:
```python
with open(filename, 'r', encoding="utf-8") as file:
  ...
```
