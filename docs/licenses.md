  <a name=top><p>&nbsp;
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1sdIwdLxZ551NChuj5Pm9FCdRRhxVdVVIPgDpNg5ZFVY/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2324.wolfware.ncsu.edu/course/view.php?id=4575">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx?folderID=d992e131-df71-4368-940d-b064012a875c">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2023</a><br>
  <a href="/README.md#top"><img   width=900 src="/docs/img/banner.png"></a></p><br clear=all>



# Licenses

## What is a license?

* Describes what you can, and more importantly, **cannot** do with a piece of software.
* A license is a legal document. You *can* and [will](https://en.wikipedia.org/wiki/Open_source_license_litigation) be sued for violating its terms.

Licenses matter. They are one of the factors in deciding if you should use a product [1]

<img src="https://media.springernature.com/lw685/springer-static/image/art%3A10.1186%2Fs42400-021-00084-8/MediaObjects/42400_2021_84_Fig2_HTML.png?as=webp">

### Why licenses?

* Explicitly describes the rights users have over their software.
* Traditional software is copyrighted: 
  * You are not allowed to use it unless you pay for it.
  * You are not allowed to modify it.
  * You are not allowed to share it.
* Open source software is licensed: 
  * You may be allowed to use it for free (what is free?)
  * You may be allowed to modify it.
  * You may be allowed to share it.
* Example: who is to blame if the software causes burns down your server room?
  * Generally, the software author is not liable for damages, even (and especially in) open-source software.

## Free Software: The free as in beer vs. free as in freedom debate

* Free as in beer: You can use it for free.
  * I buy you a beer, it's free for you.
* Free as in speech: You can do whatever you want with it.
  * You are free to say whatever you want (but you may have to pay for it).

### Why is this important?

* Very different rights as an end-user.
* The source may be open, but:
  * Can you modify it?
  * Can you then distribute it?
  * Can you profit from your modifications?
  * Can you patent it? (see: patent trolls)
  * What responsibilities do you bear as a user?
* Example: [Tivoization](https://en.wikipedia.org/wiki/Tivoization)

### Who is Richard Stallman?

* [Richard Stallman](stallman.org) is the founder of the [Free Software Foundation](https://www.fsf.org/).
* He is the author of the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.en.html) (GPL).
* He is a very controversial figure, but his work has had a profound impact on the software industry.
* Stallman is a strong proponent of free (as in speech) software, and is very vocal about his opinions.
* The FSF has contributed, among other things, to GNU and the GCC.
* If you ever hear someone talking about "GNU/Linux" (as opposed to merely "Linux"), [this](https://en.wikipedia.org/wiki/GNU/Linux_naming_controversy#Opinions) is what they are referring to.

## What license should I use?

* [Choose a license](https://choosealicense.com/) is a great resource for choosing a license.
* Generally, the Apache and MIT licenses are very common (and permissive). If you do not know (or hold opinions), you should use one of these.
  * The major difference: Apache provides an express grant of patent rights.
* The GPL (and AGPL) are strong copyleft licenses. If you want to ensure that your software remains open, you should use one of these.
  * The major difference: AGPL requires you to distribute your source code if you use the software over a network. This avoids the [Tivoization](https://en.wikipedia.org/wiki/Tivoization) problem.
  * These are also called "viral" licenses, because they require that any software that uses GPL software must also be GPL licensed.
  * The GPL has been used for many popular projects, including the Linux kernel.
  * However, companies will avoid your project like the plague if you use the GPL.
    * Which may be a plus, depending on your philosophy.
* If a GitHub repository does not have a license, [all rights are reserved and it is NOT free OR open source](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/licensing-a-repository#choosing-the-right-license). You may not modify or redistribute this code without explicit permission from the owner.
  * However, this could simply be an oversight. If you want to use the code, you should contact the owner and ask them to add a license.
  * GitHub [explains it well](https://choosealicense.com/no-license/): your options are
    * Ask the maintainers nicely to add a license.
    * Don't use the software.
    * Negotiate a private license (bring your lawyer).

## Some examples

### [MIT License](https://choosealicense.com/licenses/mit/)

* Allows commercial use
* Allows modification and distribution
* License and copyright notice must be included

### [Apache License 2.0](https://choosealicense.com/licenses/apache-2.0/)

* Allows commercial use
* Allows modification and distribution
* Allows patent use
* License and notice must be included
* Changes must be stated
* Does not grant trademark rights

# Class Activity

In the following scenarios, would you as a corporate software developer be allowed to use the software in your product?

* [Linux kernel](https://github.com/torvalds/linux)
* [Scikit-learn](https://github.com/scikit-learn/scikit-learn)
* [CKEditor](https://github.com/ckeditor/ckeditor5/)
* [Qt](https://doc.qt.io/)

# The philosophy of open source

* Open source is a philosophy, not a license.
* The [Open Source Initiative](https://opensource.org/) is a non-profit organization that promotes open source software.
* The [Open Source Definition](https://opensource.org/osd) is a set of 10 criteria that a software license must meet to be considered open source.

## Does open source mean free?

* No. Open source software can be sold.
* However, it is generally free (as in beer).
* The [Free Software Foundation](https://www.fsf.org/) is a non-profit organization that promotes free software.
* The [Free Software Definition](https://www.gnu.org/philosophy/free-sw.en.html) is a set of 4 criteria that a software license must meet to be considered free software.
* The term FOSS (Free and Open Source Software) is often used to refer to software that is both free and open source.
  * Some people prefer the term FLOSS (Free/Libre and Open Source Software) to emphasize the distinction between free as in beer and free as in speech.

## Does open source pay the bills?

* Sometimes. Some examples where it works:
  * [Red Hat](https://www.redhat.com/en)
  * [Canonical](https://www.canonical.com/)
  * [Elastic](https://www.elastic.co/)
  * [MongoDB](https://www.mongodb.com/)
  * [GitLab](https://about.gitlab.com/)
* Some examples of where it did NOT work:
  * [faker.js](https://web.archive.org/web/20210414082709/https://github.com/Marak/faker.js/issues/1046)
  * [core-js](https://github.com/zloirock/core-js/blob/master/docs/2023-02-14-so-whats-next.md)

## Parting thoughts: The Red Hat controversy (2023)

[Full article](https://sfconservancy.org/blog/2023/jun/23/rhel-gpl-analysis/)

* The Red Hat business model is to sell copies of RHEL under the GPL along with support for their customers.
* The RHEL contract states that it does not intend to contradict the allowances of the GPL (such as redistributing copies), but Red Hat reserves the right to cancel that contract if the user does so.
* Red Hat also reserves the right to "review" a customer to see how many copies of RHEL are installed.
* Red Hat's lawyers seem to argue that the GPL does not necessitate an entity from doing business with another.
* Obviously, this is not in the *spirit* of the GPL--but does it *legally* violate it?
* Until 2014, CentOS was a free alternative to RHEL, built from the RHEL "CCS" (Complete, Corresponding Source) tarball. In a sense, it acted as a check-and-balance for RHEL.
* In 2014, Red Hat acquired CentOS, and later used it as a testing ground for what might possibly be future RHEL code.
* In 2020, Red Hat ended CentOS entirely, instead changing it to CentOS Stream, a rolling-release set of packages related to RHEL.
* In 2023, Red Hat announced that the CCS would no longer be available in any way. While the GPL did not require the CCS to exist (only customers would have needed to receive the source), it was a good-faith gesture that Red Hat was not violating the GPL.

# References

[1] Zhao, Y., Liang, R., Chen, X. et al.  Cybersecur 4, 20 (2021). https://doi.org/10.1186/s42400-021-00084-8