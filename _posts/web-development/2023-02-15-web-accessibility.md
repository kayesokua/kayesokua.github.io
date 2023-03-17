---
layout: post
title: Web Accessibility
summary: A quick review of how to implement web accessibility principles in your web app
tag: web-development
---

# Intro to Web Accessibility

1. Perceivable: This principle ensures that content can be perceived by all users, including those who are blind, have low vision, or have a color vision deficiency. Examples of guidelines under this principle include providing text alternatives for non-text content, ensuring sufficient color contrast, and providing captions and transcripts for multimedia.

2. Operable: This principle ensures that users can interact with content using a range of input methods, including a keyboard, mouse, or touch screen. Examples of guidelines under this principle include providing keyboard access to all functionality, ensuring that the page can be navigated in a logical order, and providing clear and concise instructions.

3. Understandable: This principle ensures that content is easy to understand for all users, including those with cognitive or learning disabilities. Examples of guidelines under this principle include using clear and simple language, avoiding the use of jargon or technical terms, and providing consistent navigation and layout.

4. Robust: This principle ensures that content is compatible with a range of user agents, including assistive technologies such as screen readers and speech recognition software. Examples of guidelines under this principle include using valid and well-formed markup, providing alternative content for non-standard markup, and using standard document types.

(Source: [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG20/))

# WCAG Application Examples

(Example: [A Color Friendly Site](https://github.com/kayesokua/foundations-of-web-2023/tree/master/week-1))

1. Provide meaningful and descriptive headings: Use the <h1> to <h6> tags to structure your content and provide meaningful and descriptive headings that accurately reflect the content on the page. This helps users who use screen readers or other assistive technologies to navigate the page and understand the structure of the content.

2. Use alt text for images: Use the alt attribute to provide alternative text for images. This text is used by screen readers to describe the image to users who are visually impaired, and also helps search engines understand the content of the image.

3. Provide clear and concise link text: Use descriptive link text that accurately describes the destination of the link. Avoid using generic phrases like "click here" or "read more" that do not provide meaningful information about the link.

4. Ensure color contrast: Make sure there is enough contrast between the text and background color of the page to make it easy to read for users with low vision or color blindness. You can install Chrome extensions for color vision stimulation such as [Dalton for Google](https://chrome.google.com/webstore/detail/colorblind-dalton-for-goo/afcafnelafcgjinkaeohkalmfececool).

5. Provide captions and transcripts for videos and audio content: If your web page includes videos or audio content, provide captions and transcripts to make the content accessible to users who are deaf or hard of hearing.

6. Ensure keyboard accessibility: Make sure all interactive elements, such as buttons and links, can be accessed and used with a keyboard. This is important for users who cannot use a mouse or other pointing device to navigate the page.

7. Use semantic markup: Use semantic HTML tags to accurately describe the content on the page. For example, use the <article> tag to wrap a news article, and the <section> tag to group related content.

(Source: [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG20/))