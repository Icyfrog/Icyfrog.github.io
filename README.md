## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Icyfrog/Icyfrog.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for
这个页面可以用markdown语法去写，插入图片，做图片跳转啊（应该可以）等等
不过用英文看起来会更舒服一点


```html
<script src="https://code.highcharts.com/highcharts.js"></script>
<script src="https://code.highcharts.com/modules/networkgraph.js"></script>
<script src="https://code.highcharts.com/modules/exporting.js"></script>

<figure class="highcharts-figure">
  <div id="container"></div>
  <p class="highcharts-description">
    This force directed graph shows an example of a network graph, where
    the nodes represent languages and the language families they belong to.
    The nodes can be dragged around and will be repositioned dynamically.
    Network graphs are typically used to show relations in data. In this
    case, we are showing a hierarchical structure.
  </p>
</figure>

```
```javascript
// Add the nodes option through an event call. We want to start with the parent
// item and apply separate colors to each child element, then the same color to
// grandchildren.
Highcharts.addEvent(
  Highcharts.Series,
  'afterSetOptions',
  function(e) {
    var colors = Highcharts.getOptions().colors,
      i = 0,
      nodes = {};

    if (
      this instanceof Highcharts.seriesTypes.networkgraph &&
      e.options.id === 'lang-tree'
    ) {
      e.options.data.forEach(function(link) {

        if (link[0] === 'Proto Indo-European') {
          nodes['Proto Indo-European'] = {
            id: 'Proto Indo-European',
            marker: {
              radius: 20
            }
          };
          nodes[link[1]] = {
            id: link[1],
            marker: {
              radius: 10
            },
            color: colors[i++]
          };
        } else if (nodes[link[0]] && nodes[link[0]].color) {
          nodes[link[1]] = {
            id: link[1],
            color: nodes[link[0]].color
          };
        }
      });

      e.options.nodes = Object.keys(nodes).map(function(id) {
        return nodes[id];
      });
    }
  }
);

Highcharts.chart('container', {
  chart: {
    type: 'networkgraph',
    height: '100%'
  },
  title: {
    text: 'The Indo-European Language Tree'
  },
  subtitle: {
    text: 'A Force-Directed Network Graph in Highcharts'
  },
  plotOptions: {
    networkgraph: {
      keys: ['from', 'to'],
      layoutAlgorithm: {
        enableSimulation: true,
        friction: -0.9
      }
    }
  },
  series: [{
    dataLabels: {
      enabled: true,
      linkFormat: ''
    },
    id: 'lang-tree',
    data: [
      ['Proto Indo-European', 'Balto-Slavic'],
      ['Proto Indo-European', 'Germanic'],
      ['Proto Indo-European', 'Celtic'],
      ['Proto Indo-European', 'Italic'],
      ['Proto Indo-European', 'Hellenic'],
      ['Proto Indo-European', 'Anatolian'],
      ['Proto Indo-European', 'Indo-Iranian'],
      ['Proto Indo-European', 'Tocharian'],
      ['Indo-Iranian', 'Dardic'],
      ['Indo-Iranian', 'Indic'],
      ['Indo-Iranian', 'Iranian'],
      ['Iranian', 'Old Persian'],
      ['Old Persian', 'Middle Persian'],
      ['Indic', 'Sanskrit'],
      ['Italic', 'Osco-Umbrian'],
      ['Italic', 'Latino-Faliscan'],
      ['Latino-Faliscan', 'Latin'],
      ['Celtic', 'Brythonic'],
      ['Celtic', 'Goidelic'],
      ['Germanic', 'North Germanic'],
      ['Germanic', 'West Germanic'],
      ['Germanic', 'East Germanic'],
      ['North Germanic', 'Old Norse'],
      ['North Germanic', 'Old Swedish'],
      ['North Germanic', 'Old Danish'],
      ['West Germanic', 'Old English'],
      ['West Germanic', 'Old Frisian'],
      ['West Germanic', 'Old Dutch'],
      ['West Germanic', 'Old Low German'],
      ['West Germanic', 'Old High German'],
      ['Old Norse', 'Old Icelandic'],
      ['Old Norse', 'Old Norwegian'],
      ['Old Norwegian', 'Middle Norwegian'],
      ['Old Swedish', 'Middle Swedish'],
      ['Old Danish', 'Middle Danish'],
      ['Old English', 'Middle English'],
      ['Old Dutch', 'Middle Dutch'],
      ['Old Low German', 'Middle Low German'],
      ['Old High German', 'Middle High German'],
      ['Balto-Slavic', 'Baltic'],
      ['Balto-Slavic', 'Slavic'],
      ['Slavic', 'East Slavic'],
      ['Slavic', 'West Slavic'],
      ['Slavic', 'South Slavic'],
      // Leaves:
      ['Proto Indo-European', 'Phrygian'],
      ['Proto Indo-European', 'Armenian'],
      ['Proto Indo-European', 'Albanian'],
      ['Proto Indo-European', 'Thracian'],
      ['Tocharian', 'Tocharian A'],
      ['Tocharian', 'Tocharian B'],
      ['Anatolian', 'Hittite'],
      ['Anatolian', 'Palaic'],
      ['Anatolian', 'Luwic'],
      ['Anatolian', 'Lydian'],
      ['Iranian', 'Balochi'],
      ['Iranian', 'Kurdish'],
      ['Iranian', 'Pashto'],
      ['Iranian', 'Sogdian'],
      ['Old Persian', 'Pahlavi'],
      ['Middle Persian', 'Persian'],
      ['Hellenic', 'Greek'],
      ['Dardic', 'Dard'],
      ['Sanskrit', 'Sindhi'],
      ['Sanskrit', 'Romani'],
      ['Sanskrit', 'Urdu'],
      ['Sanskrit', 'Hindi'],
      ['Sanskrit', 'Bihari'],
      ['Sanskrit', 'Assamese'],
      ['Sanskrit', 'Bengali'],
      ['Sanskrit', 'Marathi'],
      ['Sanskrit', 'Gujarati'],
      ['Sanskrit', 'Punjabi'],
      ['Sanskrit', 'Sinhalese'],
      ['Osco-Umbrian', 'Umbrian'],
      ['Osco-Umbrian', 'Oscan'],
      ['Latino-Faliscan', 'Faliscan'],
      ['Latin', 'Portugese'],
      ['Latin', 'Spanish'],
      ['Latin', 'French'],
      ['Latin', 'Romanian'],
      ['Latin', 'Italian'],
      ['Latin', 'Catalan'],
      ['Latin', 'Franco-Provençal'],
      ['Latin', 'Rhaeto-Romance'],
      ['Brythonic', 'Welsh'],
      ['Brythonic', 'Breton'],
      ['Brythonic', 'Cornish'],
      ['Brythonic', 'Cuymbric'],
      ['Goidelic', 'Modern Irish'],
      ['Goidelic', 'Scottish Gaelic'],
      ['Goidelic', 'Manx'],
      ['East Germanic', 'Gothic'],
      ['Middle Low German', 'Low German'],
      ['Middle High German', '(High) German'],
      ['Middle High German', 'Yiddish'],
      ['Middle English', 'English'],
      ['Middle Dutch', 'Hollandic'],
      ['Middle Dutch', 'Flemish'],
      ['Middle Dutch', 'Dutch'],
      ['Middle Dutch', 'Limburgish'],
      ['Middle Dutch', 'Brabantian'],
      ['Middle Dutch', 'Rhinelandic'],
      ['Old Frisian', 'Frisian'],
      ['Middle Danish', 'Danish'],
      ['Middle Swedish', 'Swedish'],
      ['Middle Norwegian', 'Norwegian'],
      ['Old Norse', 'Faroese'],
      ['Old Icelandic', 'Icelandic'],
      ['Baltic', 'Old Prussian'],
      ['Baltic', 'Lithuanian'],
      ['Baltic', 'Latvian'],
      ['West Slavic', 'Polish'],
      ['West Slavic', 'Slovak'],
      ['West Slavic', 'Czech'],
      ['West Slavic', 'Wendish'],
      ['East Slavic', 'Bulgarian'],
      ['East Slavic', 'Old Church Slavonic'],
      ['East Slavic', 'Macedonian'],
      ['East Slavic', 'Serbo-Croatian'],
      ['East Slavic', 'Slovene'],
      ['South Slavic', 'Russian'],
      ['South Slavic', 'Ukrainian'],
      ['South Slavic', 'Belarusian'],
      ['South Slavic', 'Rusyn']
    ]
  }]
});

```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Icyfrog/Icyfrog.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
