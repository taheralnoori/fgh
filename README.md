# Hosting telegram bot on [Heroku](https://heroku.com) for free.
Easy way to host your python telegram bot on Heroku

## Deploying via [Heroku Toolbelt](https://toolbelt.heroku.com/) (CLI)
Install [Heroku Toolbelt](https://toolbelt.heroku.com/), then:
### Clone repository
`git clone https://github.com/Kylmakalle/heroku-telegram-bot.git`
### Edit files
1. Edit [bot.py](https://github.com/Kylmakalle/heroku-telegram-bot/blob/master/bot.py) file with your code

    1. **ATTENTION!** Do not collapse/delete/comment `some_token = os.environ[SOME_TOKEN]` style stings _(you can delete redis setup line if you do not need it)_, **do not change them with your REAL tokens**, all tokens will be setted up below in this guide!
    
    2. [More About Config Vars](https://devcenter.heroku.com/articles/config-vars)
    3. Also, don't do like [this](http://i.imgur.com/Yni1jZX.png), it's insecure, **realy.**


2. Edit [requirments.txt](https://github.com/Kylmakalle/heroku-telegram-bot/blob/master/requirements.txt) with your code's dependencies
3. Specify your python [runtime](https://github.com/Kylmakalle/heroku-telegram-bot/blob/master/runtime.txt), avaliable versions listed [here](https://devcenter.heroku.com/articles/python-runtimes)

### Go to command line
```
cd heroku-telegram-bot
heroku login
heroku create --region eu appname # create app in eu region, common regions: eu, us
heroku addons:create heroku-redis:hobby-dev -a appname # (Optionaly) installing redis
heroku buildpacks:set heroku/python # set python buildpack
git push heroku master # deploy app to heroku
heroku config:set TELEGRAM_TOKEN=123456789:AAABBBCCCDDDEEEFFFGGGHHHIIIJJJKKKLL # set config vars, insert your own
heroku config:set SOME_API_TOKEN=qwertyuiop1234567890
                ...
heroku ps:scale bot=1 # start bot dyno
heroku logs --tail # If for some reason it’s not working, check the logs
heroku ps:stop bot #stop bot dyno
```

## Deploying via [Heroku Dashboard](https://dashboard.heroku.com) (GUI)
1. [Fork](https://github.com/Kylmakalle/heroku-telegram-bot/fork) this repo to your account. 
2. [Edit files](https://github.com/Kylmakalle/heroku-telegram-bot#edit-files)
3. Go to [Dashboard](https://dashboard.heroku.com), login, Press _New_ and choose _Create new app._
4. Fill in an _App Name_ and choose _Runtime Region._
5. Connect your GitHub repo at _Deploy_ page.
6. Setup **Automatics deploys** _(Optionaly)._
7. _Deploy a GitHub branch._
8. Then go to a _Settings_ page, click _Reveal Config Vars_ and then add your own, for example:
![Config Vars](http://i.imgur.com/C3cmphh.png)
9. **Finally**, go to the _Resources_ page.
    1. Install _Heroku Redis_ add-on _(Optionaly)_
    2. Press on a small pen button, move slider and then click _Confirm_, that will start bot dyno.
    3. Simply move slider back if you need to stop bot dyno, remember to click _Confirm_.
    4. If for some reason it’s not working, check the logs here 
    
    ![Logs](http://i.imgur.com/rIHU6zF.png)

### More about
- https://devcenter.heroku.com/articles/dynos
- https://devcenter.heroku.com/articles/config-vars
- https://devcenter.heroku.com/articles/heroku-redis
- https://devcenter.heroku.com/articles/error-codes

Thanks to [Roman Zaynetdinov](https://github.com/zaynetro) for awesome and easy CLI guide.
<h1 dir="auto"><a id="user-content-deploy" class="anchor" aria-hidden="true" href="#deploy"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Deploy</h1>
<p dir="auto"><a href="https://heroku.com/deploy?template=https://github.com/Lucy-Robot/zip_files_bot" rel="nofollow"><img src="https://camo.githubusercontent.com/6979881d5a96b7b18a057083bb8aeb87ba35fc279452e29034c1e1c49ade0636/68747470733a2f2f7777772e6865726f6b7563646e2e636f6d2f6465706c6f792f627574746f6e2e737667" alt="Deploy" data-canonical-src="https://www.herokucdn.com/deploy/button.svg" style="max-width: 100%;"></a></p>
