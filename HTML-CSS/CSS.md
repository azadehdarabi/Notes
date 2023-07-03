# justify-content

*Use the `[align-items](https://www.w3schools.com/cssref/css3_pr_align-items.php)` property to align the items vertically.*


<pre>
justify-content: flex-start|flex-end|center|space-between|space-around|space-evenly|initial|inherit;
</pre>

![[Pasted image 20230703013421.png]]


# display

The `display` property specifies the display behavior (the type of rendering box) of an element.

![[Pasted image 20230703090338.png]]
![[Pasted image 20230703090406.png]]

[https://www.w3schools.com/cssref/pr_class_display.php]

# white-space

The `white-space` property specifies how white-space inside an element is handled.

![[Pasted image 20230703102926.png]]

# @media

The `@media` rule is used in media queries to apply different styles for different media types/devices.

Media queries can be used to check many things, such as:

- width and height of the viewport
- width and height of the device
- orientation (is the tablet/phone in landscape or portrait mode?)
- resolution


<pre>
@media not|only _mediatype_ and _(mediafeature_ and|or|not _mediafeature)_ {  _CSS-Code;_}
</pre>


meaning of the **not**, **only** and **and** keywords:

**not:** The not keyword inverts the meaning of an entire media query.

**only:** The only keyword prevents older browsers that do not support media queries with media features from applying the specified styles. **It has no effect on modern browsers.**

**and:** The and keyword combines a media feature with a media type or other media features.

They are all optional. However, if you use **not** or **only**, you must also specify a media type.