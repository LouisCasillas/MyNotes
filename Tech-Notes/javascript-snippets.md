# JavaScript Snippets

- get all link URLs from some area on a page
document.querySelector('center').querySelectorAll('a').forEach((link, index) => { console.log(link.href) });