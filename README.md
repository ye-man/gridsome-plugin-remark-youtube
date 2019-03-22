# Gridsome Remark Twitter

This is a plugin for [Gridsome](https://gridsome.org/)'s chosen markdown engine, [Remark](https://remark.js.org/), and allows you to embed [YouTube](https://www.youtube.com/) videos in [markdown](https://daringfireball.net/projects/markdown/) files.

## Installation

```bash
npm i gridsome-plugin-remark-youtube
# yarn add gridsome-plugin-remark-youtube
```

## Loading

```js
module.exports = {
  plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'blog/**/*.md',
        route: '/blog/:year/:month/:day/:slug',
        remark: {
          plugins: [
            ['gridsome-plugin-remark-youtube']
          ]
        }
      }
    }
  ]
}
```

## Options

There are options to change width of the video, and whether the video is left aligned or centred:

- **width** Default `100%`.  Set to any valid CSS width.
- **align** Default `0`.  The default left aligns the video. Set to `auto` to align the video centrally.

Loading with options:

```js
module.exports = {
  plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'blog/**/*.md',
        route: '/blog/:year/:month/:day/:slug',
        remark: {
          plugins: [
            ['gridsome-plugin-remark-youtube', {width: '500px', align: 0}]
          ]
        }
      }
    }
  ]
}
```


## Usage

This plugin uses the same markdown syntax as the Gatsby plugin, with backticks and a youtube: prefix, followed by the YouTube URL. Any valid YouTube URL _should_ work.

```markdown
`youtube:https://www.youtube.com/watch?v=dQw4w9WgXcQ`

or

`youtube:https://www.youtube.com/embed/dQw4w9WgXcQ`

or

`youtube:https://youtu.be/dQw4w9WgXcQ`
```

## Output

### Video

This is how the video should appear on the screen:

<div style="width: 100%; margin: 0 auto;"><div style="position: relative; padding-bottom: 56.25%; padding-top: 25px; height: 0;"><iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe></div></div>

## Generated HTML

This is the HTML that is being generated by the plugin and injected into the page:

```html
<div style="width: 100%; margin: 0 auto;"><div style="position: relative; padding-bottom: 56.25%; padding-top: 25px; height: 0;"><iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/dQw4w9WgXcQ"></iframe></div></div>
```

## License

MIT

## Credit

Some of the code in this plugin was copied from the Gatsby plugin for embedding YouTube videos in markdown:

https://github.com/ntwcklng/gatsby-remark-embed-youtube

To figure out how to convert the above plugin to a Gridsome plugin, I cribbed from Gridsome's Twitter Remark plugin:

https://github.com/danvega/gridsome-plugin-remark-twitter
