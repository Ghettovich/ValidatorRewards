# ValidatorRewards
An XRP community initiative to incentivize validators

This repo is still under construction. Here is how this app currently works:

1. validator data will be retreived thorugh the XRPL data API (https://xrpl.org/data-api.html). These functions are included in rippleStats.py
2. logic surrounding what makes a good validator is included in validatorScoreCard.py. ultimately, all business logic should be encapsulated in the grep_all function.
3. test.py is where I've been testing these functions. Currently test.py pulls payment pointers and node public keys from the config file, gets a report for the past 24 hours, makes sure they were good, and if so, adds them to a trigger file. 
4. Reward.sh is where I pull the reward (which is the bounty, currently .1XRP and floor divide it by the number of good validators), and the payment pointers of the good validators, then run an ilp-spsp send command to each of the payment pointers.

Config.py includes an object formatted like this:

```
{
    publicKey:paymentPointer
}
```
Getting your validator added will involve submitting a pull request with a comment, the comment must be a signed SHA256 message, decrypted using your public key. The message must be your ILP payment pointer. If you are able to successfully do that, I'll add you to the config. Alternatively, if I know you already, you can DM me on twitter or submit a pull request.


Want to contirbute? DM me on twitter: https://twitter.com/AJ58O


Installation/Running:

If you don't ahve moneyd installed and configured yet, you will need to do that. Here's an extremely overkill script that can help you do that: https://github.com/AJ58O/K-ILP-it-with-fire

```
$ git clone https://github.com/AJ58O/ValidatorRewards.git
$ cd ValidatorRewards
$ pip3 install requirements.txt
$ bash run.sh
```

Still trying to dockerize everything. Long term plan is to deploy this onto codius.
