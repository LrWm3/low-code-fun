# low-code-fun

Low code fun

## Background

Chris Sawyer did all of the programming for Roller Coaster Tycoon in two years using x86 asm
after creating Transport Tycoon. I am not sure how long it took him to originally create
Transport Tycoon, but it seems as though it was done on a similar timeline.

Yet, I believe even most senior software developers would be challenged to replicate such a feat,
even given access to any software development language & frameworks on a timeline of 3 years.

Why is it that Chris Sawyer was able to do this? I believe the answer is because he was good at
creating highly modular software using code.

I think it's fair to say that most of us are not that good at creating highly modular software using code,
event when given access to an abundance of resources & freedom in choices around technology & tooling.

Software development is inherently hard to do. We primarily do it with code written in text.

Without going through the core challenges which make software development difficult, I think it's fair to say
there's some desire to have technology stacks which take advantage of more of what we have to offer than
what we can do with text files.

However, the current text file approach has been the way we've gone about things for over 50 years.
There are a few significant advantages this approach has over many of the more modern no-code approaches.

Some of these areas will need to be re-explored as we learn to deploy new techniques and tools for software
development.

- Understanding of version control
- Understanding of testing and verification
- Understanding of how to build plugin & modular architectures
- IDE Debugging

## This repo

This repository is used to explore nocodDB, an open-source Airtable offering.

## Usage

To start running this example, run

```
docker-compose up
```

## Notes

I'm going to play around with building out a site that users can upload content to and view through the UI.

The initial database is empty. I create a table called 'content_metadata' through the UI.

I add the fields 'content_metadata' with 'title, description'

I add a new table 'content_link'. Content can have lots of links, but each link is associated with only one 'content_metadata' row.

Content links have a reference to content metadata, and a url field.

I create a new table 'content_type', to store the type of content we're storing.

I add the following rows; 'file', 'vid', 'img', 'vid_stream', 'audio'. This will correspond to the type of resource we're storing.

Now, 'content_type' references this table as well, to support the enum.

Next, we add 'tags' to exercise many-to-many relationships.

The tags table has 'key' and 'value' columns. 'key' is non-null, and 'value' is optional.

Next, we create 'tag_content_metadata_link' to store references between 'content_metadata'

> I tried creating 'tag_content_link' and then deleting it. But I got an error and the table did not appear to delete!

But then I decided I only have so much time for this and I better shorten things up a bit.

I just noticed the id column is by default numeric counting up. Questionable?

I can't figure out how to delete rows I create accidentally.

I eventually hit an auth issue on the GQL query.

## Final Thoughts

The App Store aspect of this product is a cool idea. Having storage, chat and other types of things built into the database level is cool.

I think I understand the general idea of something like airtable. I just feel like something is missing.

I think inherently the problem boils down to something like this:

1. Spreadsheets are the best tools for semi-technical people to play with data. Even then, building spreadsheets is a specialized skill
2. An SQL database is the best tool for analysts, researchers and automated systems to work with data. This is because structured data and indices provide a lot of power in terms of both the volume of records under management, and the complexity of the questions which can be answered.
3. Additionally, authentication, user management, monitoring, alarming and billing adds yet another layer of complexity on top of this which is typically required for performing shared analysis
4. For people with limited technical skills, it is unclear what the best tool is. It may be a notebook, or a hand-written table and a calculator. Or it may be using money to pay other people to
   manage this kind of work. I am not sure.

The most popular products seem to combine authentication and authorization & then slant towards either spreadsheet types or SQL relational types. Additionally, there is still a yet unserved
group of people which cannot make use of spreadsheets.

The remaining questions become:

- How can we serve people who can't use spreadsheets at all? What tools will best help them answer questions relevant to them?
- How can we translate work performed in spreadsheets into something more structured which can be used by automated systems and analysts?
- How can we translate private automated systems used by automated systems and analysts into public facing ones which can be used by anyone?
