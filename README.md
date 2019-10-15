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
