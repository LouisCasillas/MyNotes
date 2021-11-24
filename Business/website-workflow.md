# Website Workflow
- TODO: re-write in Markdown

0) Download automated script that sets up the Dev/Publishing environment
    • Should try to automate steps 1-2

1) Install Vagrant and build the box
    • Vagrant - https://www.vagrantup.com/

2) Install dependencies for tools
    • General tools
        ◦ FTP/SFTP/….
        ◦ Nodejs
    • Dependency management
        ◦ Yarn - https://yarnpkg.com/en/docs/getting-started
    • Source code management
        ◦ Git
    • Editor
        ◦ Visual Studio Code
            ▪ Plugins?
    • Flat file site generation
        ◦ Gatsby
            ▪ GatsbyCLI 
        ◦ React.js
            ▪ 30 days with React - https://github.com/fullstackreact/30-days-of-react
        ◦ Typography.js
    • CMS
        ◦ NetlifyCMS - https://www.gatsbyjs.org/docs/netlify-cms/
    • Code formatting/Linting
        ◦ JS
            ▪ Prettier - https://prettier.io/
            ▪ ESLint
            ▪ StyleLint - https://stylelint.io/
        ◦ TypeScript
            ▪ TSLint - https://palantir.github.io/tslint/
        ◦ CSS
            ▪ StyleLint - https://stylelint.io/
            ▪ PostCSS - https://postcss.org/
    • Code tools
        ◦ JS
            ▪ TypeScript
        ◦ CSS
            ▪ Sass	
    • Unit Testing
        ◦ JS
            ▪ Jest - https://jestjs.io/
        ◦ React.js
            ▪ Enzyme - http://airbnb.io/enzyme/
        ◦ CSS
            ▪ Barista - https://github.com/helpscout/seed-barista
        ◦ Website
            ▪ Selenium
            ▪ Nightmare - http://www.nightmarejs.org/
x) Build new Git repo for a new website or checkout existing websites Git repo
    • IF starting a new website clone files from skeleton Git repos for starter website
        ◦ Create new gmail address for the website that forwards to LouisCasillasEnterprises@gmail.com

x) Create content in #staging branch

x) Run jobs over new content
    • Get any new comments from DB (Amazon DynamoDB)
    • Build JS search index
    • Gather related Youtube videos, popular websites, … ?
    • Check all links for 404s.
    • Check all links for changed information
        ◦ Setup file with links and some expected text, alert if the expected text isn’t found
        ◦ Update number of times the link has been followed?
    • Update all affiliate links with “hidden” links
        ◦ http://test/2390923 => http://human-readable-link
        ◦ 

x) Deployment to Netlify staging

x) Review new content and run user acceptance testing

x) Final optimization and testing
            ▪ JS
                • webpack-bundle-analyzer - https://www.npmjs.com/package/webpack-bundle-analyzer
                •  import-cost for Visual Code
                • https://www.npmjs.com/package/source-map-explorer
                • https://github.com/samccone/bundle-buddy
                • Code Coverage - https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage
                • Minifier
                    ◦ JS
                        ▪ Uglify - http://lisperator.net/uglifyjs/
                    ◦ CSS
                        ▪ CSSNano - https://github.com/cssnano/cssnano
                        ▪ 
                    ◦ HTML
                        ▪ https://github.com/kangax/html-minifier
                        ▪ 
            ▪ CSS
            ▪ Test My CSS - https://github.com/macbre/analyze-css
                • Code Coverage - https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage
            ▪ 
            ▪ HTML
                • HTML Hint - http://htmlhint.com/
                • Link checking - https://www.npmjs.com/package/broken-link-checker
            ▪ Images
            ▪ gif - https://github.com/kornelski/giflossy
            ▪ jpeg - JpegOptim 
            ▪ PNG - OptiPNG
            ▪ SVG - https://github.com/RazrFalcon/svgcleaner
            ▪ General
                • Find duplicate code - https://github.com/rdgd/twly
            ▪ Site
                • Speed/Performance
                    ◦ Tools
                        ▪ LightHouse - https://developers.google.com/web/tools/lighthouse/
                        ▪ https://webpagetest.org/
                        ▪ https://testmysite.thinkwithgoogle.com/
                        ▪ https://developers.google.com/speed/pagespeed/insights/
                        ▪ https://tools.pingdom.com/
                    ◦ https://developers.google.com/web/fundamentals/performance/rail
                    ◦ https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/javascript-startup-optimization/
                    ◦ https://houssein.me/thinking-prpl

x) Deploy to #master branch for production

x) User acceptance testing for the new content on the live website

Extra
x) Monitoring
        ◦ JS
            ▪ Send console errors to server endpoint - similar to: https://sentry.io/welcome/
        ◦ Metrics
            ▪ Google Analytics
                • https://analytics.google.com/analytics/web/
        ◦ Live page down monitoring?
x) Create my own link shortener
    • Ideas:
    • https://aws.amazon.com/blogs/compute/build-a-serverless-private-url-shortener/
    • Use VPS for geolocation redirection
    • Track number of times links have been clicked
    • “Hide” affiliate links
x) Automatically translate the site into new languages
    • Change the URL and all affiliate links if necessary
        ◦ http://test.com/page1 => http://test.com/jp/page1
    • Follow Google best practices if doing this
        ◦ https://support.google.com/webmasters/answer/6059209?hl=en&topic=2371325&ctx=topic&visit_id=636704779560335026-397763554&rd=1
    • Maybe use the Google auto-translate
        ◦ https://www.websitebuilderexpert.com/how-to-build-a-multi-language-website/
