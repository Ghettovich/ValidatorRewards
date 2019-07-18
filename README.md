# ValidatorRewards
An XRP community initiative to incentivize validators

### How this app currently works:

1. validator data will be retreived thorugh the XRPL data API (https://xrpl.org/data-api.html). These functions are included in rippleStats.py
2. logic surrounding what makes a good validator is included in validatorScoreCard.py. ultimately, all business logic should be encapsulated in the grep_all function.
3. test.py is where I've been testing these functions. Currently test.py pulls payment pointers and node public keys from the config file, gets a report for the past 24 hours, makes sure they were good, and if so, adds them to a trigger files. 
4. Reward.sh is where I pull the reward (which is the bounty, currently .1XRP, floor divided by the number of good validators), and the payment pointers of the good validators from the trigger files, then run an ilp-spsp send command to each of the payment pointers.

### Adding your validator

Config.py includes an object formatted like this:

```
{
    "publicKey":"paymentPointer"
}
```

1. Fork the repo
2. Add your node/validator to the object in config.py
3. Submit a pull request
4. Offer some sort of proof that you own this validator

If you don't know how to do 1-3, reach out to me on twitter: https://twitter.com/AJ58O


### Installation/Running:

If you don't have moneyd installed and configured yet, you will need to do that. Here's an extremely overkill script that can help you do that: https://github.com/AJ58O/K-ILP-it-with-fire

```
$ git clone https://github.com/AJ58O/ValidatorRewards.git
$ cd ValidatorRewards
$ pip3 install requirements.txt
$ bash run.sh
```

### Things to do:

1. Still trying to dockerize everything.
2. Test.py waits 15 seconds for moneyd to start up. It would be better for it to wait until the stdin shows the message "connector ready" or whatever the success message is.


**Want to contirbute?** DM me on twitter: https://twitter.com/AJ58O
