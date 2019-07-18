# ValidatorRewards
An XRP community initiative to incentivize validators

### How this app works:

1. Validator data is retreived thorugh the XRPL data API (https://xrpl.org/data-api.html). These functions are included in rippleStats.py
2. logic determining what makes a good validator is included in validatorScoreCard.py. All business logic is executed in the grep_all function
3. test.py pulls payment pointers and node public keys from the config file, gets a report for the past 24 hours, if the validator is good, adds them to a trigger files. 
4. Reward.sh reads the reward amount and payment pointers from files and runs an ilp-spsp send on each of the payment pointers.

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
