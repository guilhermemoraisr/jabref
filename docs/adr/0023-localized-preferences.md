# Localized Preferences

* Status: proposed
* Date: 2021-09-01

## Context and Problem Statement

Currently, JabRef uses some localized preferences. We want to remove the Localization-dependency from the JabRefPreferences and move the Localization to where the String is used.
The problem is how to store the default values.

## Considered Options

* Localized defaults
* Store changed preferences
* Store the unlocalized string

## Decision Outcome

Chosen option: "Store the unlocalized string", because Achieves goals without requiring too much refactoring and without (known) downsides.

## Pros and Cons of the Options

### Localized defaults

The default preference values are localized. That means that if JabRef does not find a value of the preference, it creates puts a default value. This value is the localized one.

* Good, because This is the implementation as of August, 2021

### Store changed preferences

Store the preference only when it was changed by the user. Otherwise, leave it empty.

* Good, because When a consumer gets such an empty preference, it knows that it needs to read the default and localize it.
* Bad, because this won't work if users actually want something to be empty.

### Store the unlocalized string

The string is stored in English language. Consumers then check the String they got as a preference against the defaults. If it matches, localize it. Otherwise, use it.
