---
layout: post
title:  "Welcome to Flying Swiftly!"
date:   2022-01-08 16:18:25 +0800
categories: orginal
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight swift %}

import XCTest
@testable import FitNess

class RootViewControllerTests: XCTestCase {

  var sut: RootViewController!
  
  override func setUp() {
    super.setUp()
    sut = loadRootViewController()
    sut.reset()
    AlertCenter.instance.clearAlerts()
  }
  
  override func tearDown() {
    sut = nil
    AlertCenter.instance.clearAlerts()
    super.tearDown()
  }
  
  // MARK: - Alert Container
  func testWhenLoaded_noAlertsAreShown() {
    XCTAssertEqual(AlertCenter.instance.alertCount, 0)
    XCTAssertTrue(sut.alertContainer.isHidden)
  }

  func testWhenAlertsPosted_alertContainerIsShown() {
    // given
    let exp = expectation(forNotification: AlertNotification.name,
                          object: nil, handler: nil)
    let alert = Alert("show the container")

    // when
    AlertCenter.instance.postAlert(alert: alert)

    // then
    wait(for: [exp], timeout: 1)
    XCTAssertFalse(sut.alertContainer.isHidden)
  }
}


{% endhighlight %}

[FetchMee](https://twitter.com/jyrnan/status/1440293166150651912)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/


