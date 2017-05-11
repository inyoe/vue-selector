# vue-selector

# demo
http://demo.rabifoo.com/#/selector

### Usage

```javascript
import swiper from './plugin/selector'

Vue.use(selector)
```

html:
````html
<div class="item">
  <label>Game</label>
  <selector v-model="games"></selector>
  <p>Game: {{games.option[games.selected].value}}</p>
</div>
````

js:
````javascript
games: {
  selected: 0,  //默认选择项
  option: [
    {
      text: 'World of Warcraft',
      value: 'wow'
    },
    {
      text: 'Diablo',
      value: 'd3'
    },
    {
      text: 'OverWatch',
      value: 'pp'
    },
    {
      text: 'Hearth Stone',
      value: 'hotel'
    },
    {
      text: 'StarCraft',
      value: 'sc'
    }
  ]
}
````
