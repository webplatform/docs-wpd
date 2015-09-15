---
title: 0513 raw mtg notes
uri: 'WPD:Community/Meetings/General/2014/0513 raw mtg notes'

---
Also [archived in the mailing list](http://www.w3.org/mid/CAFDDJ7y0Q8n=0Jm9ySxTyyHsCXT7J+_boFUYE8UWGwwnbJJfeA@mail.gmail.com)

## <span>Presents</span>

On IRC, and call:

-   AmeliaBR (scribe)
-   renoirb
-   shepazu (chair)
-   Julee
-   Eliot
-   JenSimmons

On IRC:

-   eliezerb
-   jswisher

## <span>Topics</span>

-   Discussing scheduling of telecon re DocSprint Europe
-   Page formatting
-   Readiness markers

## <span>Notes</span>

### <span>Discussing scheduling of telecon re DocSprint Europe</span>

    shepazu & Julee:  Discussing scheduling of telecon re DocSprint Europe
    ... was scheduled for Friday, but will try to reschedule
    eliot:  reminder that Jay had asked for suggestion of topics for DocSprint
    Julee:  Should anyone be working on the Javascript import review?
    eliot:  If anyone wants to sure, but he can do it in-house at MS if
    necessary
    * jswisher is in the channel but not on the call
    shepazu: I don't think it would hurt to invite people to work on JS clean-up

    eliot: would be a task for people who don't have a lot of other experience

    shepazu:  if SVG is main focus, need to make sure people are familiar

    ... will discuss further when everyone involved with DocSprint is available
    (i.e., rescheduled telcon)

### <span>Page formatting</span>

    All agreed, minus sarcasm from shepazu, that tables are ugly and confusing
    Jen:  Should only have title, not path, should be list not table
    <AmeliaBR> http://docs.webplatform.org/wiki/css/properties
    <AmeliaBR> ^^Example of inline query structure

    <AmeliaBR> Alternative result formats for queries:
    http://semantic-mediawiki.org/wiki/Help:Result_formats

    jensimmons: Would be nice to condense long lists as hierachy, possibly
    toggle-able

    AmeliaBR:  I can work on this eventually, but have other commitments already

    shepazu:  is there someone else who can experiment with these queries to
    figure out better output?  Can we reach out beyond our usual core of
    contributors?

    <+eliezerb> AmeliaBR: I did some work with SMW Queries

    <@shepazu> eliezerb, do you have time to help with this formatting issue?

    <+eliezerb> shepazu: Yes, I just need to fresh my memory about those
    queries, but I'm always here to help

    <+eliezerb>

    <@shepazu> eliezerb, let's talk after the call

    <+eliezerb> cool

    <eliot> Can I throw out there that this could be a list with more details
    on hover or another means?

    <AmeliaBR> Plan would be (a)  replace index tables with query lists (b)
    examine more nuanced options when lists are really long

### <span>Readiness markers</span>

    jensimmons:  discussing different sample images from emails she sent out

    <@renoirb> shepazu:
    http://www.w3.org/mid/CAB0bRKOCzGOzrHESCEgT2mNecvyOkQ+bU_19wvpWFPJeie2FHw@mail.gmail.com

    <@renoirb> is one of them

    <@renoirb> This one has a lot of images
    http://lists.w3.org/Archives/Public/public-webplatform/2014May/0044.html

    eliot: I find angled ribbon distracting

    shepazu, renoir, AmeliaBR agree

    renoirb: sidebar is neater

    eliot: also similar to status markers on W3 specs

    shepazu: agreed.  Was that the intention?

    jensimmons: not originally, but I recognized the similarity

    ...there are two versions: square stripe up to the bar, or with a circle
    end to mimic the logo

    eliot:  I like the rounded version, webplatform's version of w3 status
    markers

    renoirb: I like look, but I don't know how to do this without abuse of
    absolute positioning

    jensimmons:  should be possible, would like to have top of stripe move with
    page but words stay fixed as you scroll

    * renoirb +1 vertical bar + rivet

    jensimmons:  also still need to work with colours

    ...what do people think?  Home page colour set versus more intuitive
    green-red sequence

    ...want colour meaning to be obvious when someone first lands on a page

    eliot: is the green-yellow-red meaning culturally independent?

    jensimmons: green-yellow-red traffic signals seem to be fairly universal

    julee: with the words as well, there is flexibility in the colours

    eliot: because of the words, we can choose colours that are a little more
    attractive

    jensimmons:  colours should always be secondary for accessibility reasons,
    but colours shouldn't be confusing

    renoirb: another option is to incorporate icons/shapes

    shepazu: don't want to dwell on colours, but am concerned about contrast
    issues with yellow background

    ...could just swap purple and red from current colour scheme

    <@renoirb> +1 on colors choice to Jen. BTW, I like the color choice anyway

    julee: we can always do something, then adjust based on feedback

    <@renoirb> Anyway, we aren't stuck on old IE versions so text and colors
    won't need images

    shepazu: work on the design and layout first, changing colours later is easy

    jensimmons: worried about terms "coming later" is problematic, suggests
    that people shouldn't work on this

    AmeliaBR: "not started" might be confusing on an unreviewed import page

    * renoirb just thought about "needs some love"

    <@renoirb> +1 "needs work"

    shepazu:  "needs work"

    <@renoirb> q+

    jensimmons:  "needs work" is good, since it encourages contribution

    shepazu:  sounds good for now, this isn't hard to change later

    ...given the prominence, is it clear that status refers to article not specs

    AmeliaBR:  example text box was "This article is..." but that's lost in
    graphic examples

    renoirb: although we want to move warnings out of the way for good content,
    maybe a big warning box is a good idea in Not Started pages

    jensimmons:  how to efficiently inform people of ongoing projects?

    shepazu: should we not have a marker on pages that are ready to use

    jensimmons: I think it's important to establish a consistent pattern

    ...maybe two years from now, when most pages are ready to use, we can drop
    the notice

    shepazu: I like the sidebar status concept, when status is more consistent
    in future we can consider a different way of doing this

    ...e.g. for now we're using compatibility as tables, similar to MDN, in
    future that might change

    (tangent on how to display compatibility info tabled until future)

    jensimmons: for now, let's use "Ready to Use"

    AmeliaBR: should we still put the template up for now, with a <div> for the
    text?

    jensimmons:  Yes, add a line of html at a place where it makes sense as
    plain text/screen reader/api

    renoirb: might be able to add info in http headers as well

    <@renoirb> ... I think its possible to query through PHP result of your
    work AmeliaBR and i'd do HTTP headers.

    shepazu: Action to AmeliaBR: please go ahead with template to add this info
    for jensimmons to use for styling

    shepazu: talking about scheduling template updates

    <+jensimmons> <div class=“readiness-marker”>This article is <a
    href=“”>Ready to Use</a></div>

    <+jensimmons> That HTML should also be the fallback for any browsers that
    can’t use the CSS we write to make the text verticle. Old IE, etc.

    <@renoirb> ... renoirb asks to know when, he'll take care of ensuring it
    doesnt blow the server

    <@renoirb> note that the next site in /upgrade/ will possibly prevent
    current problems

    shepazu:  IMPORTANT note: any changes to templates should be scheduled and
    renoirb should be warned, so that the server queue doesn't crash

    <@renoirb> Thanks for touching base with me AmeliaBR

    renoirb:  timing not essential, but I need to know.  Hopefully,  next
    server upgrade will take care of problem

    <@renoirb> server upgrade is basically MediaWiki+SMW software upgrade

    <@renoirb> (Ubuntu server version isn't related to the possible factor of
    improvement on this particular issue)

    <@renoirb> SMW problem is basically: A widely used template called into
    another page creates jobs inside mediawiki.  There is a bug in SMW when MW
    job queue is run that creates sub tasks... creating thousands and thousands
    of jobs.

    <@julee> Sorry. Have to run…

    shepazu: Once we have readiness flags up, we will have to go through and
    set good pages to ready/almost done/etc.

    shepazu:  if we're going to be walking through and cataloguing, there is
    also the API syntax index issues, although that could also be done at a
    DocSprint

    ...we need to figure out timing.  Should we still be doing this on test
    wiki when we don't have a scheduled?

    jensimmons:  we should have a default, maybe nothing prints if no value
    set, or just a small line out of sight?

    AmeliaBR: we can do that, just not print if there is no value set in the
    form

    jensimmons: are we still going to have details note box?

    AmeliaBR: last plan was details/notes would be in form, but not in the page

    ...the status would link to definition page, which would also tell people
    to edit page to see details

    shepazu: What's the plan?

    AmeliaBR:  I will get things ready to go on test wiki, then roll out on
    main.  What is default?

    jensimmons: default should be nothing displays until the page status has
    been set.

    <@renoirb> We can dry run on the /upgrade/ wiki too

    jensimmons: I will be working on the CSS

    <@renoirb> jensimmons, AmeliaBR ^

    Thanks renoirb.

    <@renoirb> I can make you admin there, or just drop the database and import
    a new snapshot off of the live site.

    <+jensimmons> Thanks everyone!!!! I think this readiness state stuff is
    really good!

    <+jensimmons> I will help people understand WPD — how to use it, and how to
    help

    <@renoirb> Next time, AmeliaBR, i'll scribe

    <AmeliaBR> renoirb:  whichever works for you (re upgrade wiki).  And I'll
    remind you if you're late next week!

    <@renoirb> np AmeliaBR.

    <@renoirb> I'm busy full time on authentication ATM, if you have technical
    worries, just ping me