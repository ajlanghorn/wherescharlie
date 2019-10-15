# Where's Charlie?

Sometimes, Charlie gets lost. And, when he does, we need to know where he's got to. So, what better way to make this mind-numbingly boring and yet so-often commonplace task repeatable than by asking everyone's favourite speaker to help out?!

```
Alexa, ask Where's Charlie to find Charlie.
```

## Batteries partially included

This repository contains some, but not all, of the code you'll need to either recreate, or request an update to, the existing skill. Here's a brief primer.

### Invocation Model (`invocationModel.js`)

The invocation model is, essentially, the gateway between Alexa and this skill. It tells Alexa what to do when we ask for the skill. Therefore, it contains details about what the skill is called (which helps power "Alexa, open <skill>"), alongside setting up prerequisite intents. Each Alexa skill requires, at a minimum, the following intents:

- `AMAZON.FallbackIntent`
- `AMAZON.CancelIntent`
- `AMAZON.HelpIntent`
- `AMAZON.StopIntent`
- `AMAZON.NavigateHomeIntent`

Each of these intents is documented, canonically, in the Alexa documentation. A good place to start to understand invocations is [this page](https://developer.amazon.com/docs/custom-skills/understanding-how-users-invoke-custom-skills.html) on the docs, which looks at invocation from a voice UX perspective.

We also need a custom intent to actually be able to respond to our skill's name in a variety of ways. In this repository, we do this with the `locateCharlieIntent`, and provide a number of samples (which effectively act as synonyms to launch the skill), including:

- `Locate Charlie`
- `Where is Charlie`
- `Find Charlie`
- `Wheres Charlie`

Samples can't contain punctuation, hence the bloody awful grammar in there.

### Lambda function (lambda/)

The `lambda/` directory is, essentially, our back-end. Think of it as the server in the client-server model. Inside, you'll find three files - `index.js`, `util.js` and `package.json`. For our purposes, the majority of the time, we'll be in `index.js`. The `package.json` file contains metadata about our Lambda function (since it's written in NodeJS, and we therefore should stick to its conventions). The `util.js` file creates some connections to other AWS services, such as S3, using [Signature Version 4](https://docs.aws.amazon.com/general/latest/gr/signature-version-4.html).

Of all of the code in `lambda/index.js`, the only bit you really need to consider editing is that in the `FactsData` const. These phrases are those uttered by Alexa in response to our requests. To add new facts, add them to the end of the `FACTS` dictionary, where each entry is separated by a trailing comma unless it is the final entry (when it is suffixed with nothing whatsoever).

Deployment is, right now, manual, since this skill runs from my Amazon account. As such, pull requests welcome, and I'll merge any that I see fit.

## Pull requests welcome

I welcome contributions to the repository, which is meant in light-hearted jest. Any that are actually offensive, don't make sense or are otherwise in any way upsetting to myself, the subject matter or anyone else will not be merged. You've been warned. Play nice.
