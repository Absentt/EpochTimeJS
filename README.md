# EpochTimeJS
PAPI epoch time get for player. First ever script sooo probably ineffecient and not the best way, but it works c:

## JS Epoch Time Set Up
### Firstly
- Do: /papi ecloud download javascript
- Do: /papi reload

### Secondly
- Go to: plugins/PlaceholderAPI/javascripts
- Upload: epoch_time.js into /javascripts
- Go to: plugins/PlaceholderAPI
- Open: javascript_placeholders.yml
- Paste in the following:
```yml
epoch_time:
  file: epoch_time.js
  engine: nashorn
```

- Save javascript_placeholders.yml
- Do: /papi reload

### Thirdly - For DeluxeMenus
- Open: plugins/DeluxMenus/gui_menus
- Open up the menu you would like to set a join-date view_requirement for
- Paste in the following
```yml
    view_requirement:
      requirements:
        <NAME>:
          type: javascript
          expression: '%javascript_epoch_time% <true/false math-expression>'
```
This is where you use your boolean (<,>,=,<=,>=,!=, etc)

You will also need to grab the time from https://currentmillis.com/ using the converter to get the value you want.


### Example:
In this example I wanted to give a suffix only to people who joined before a certain date.
```yml
  'og':
    material: name_tag
    display_name: '&8{&e✯&8}'
    lore:
      - '&eSpecial &7tag for our'
      - '&7early supporters!'
    slot: 9
    priority: 17
    view_requirement:
      requirements:
        joindate:
          type: javascript
          expression: '%javascript_epoch_time% <= 1632913200000'
    left_click_commands:
    - '[console] lp user %player_name% meta setsuffix 10000 " &8{&e✯&8}"'
    - '[message] &aSuffix successfully changed!'
    right_click_commands:
    - '[console] lp user %player_name% meta setsuffix 10000 " &8{&e✯&8}"'
    - '[message] &aSuffix successfully changed!'
  'nog':
    material: barrier
    display_name: '&8{&e✯&8}'
    lore:
      - '&eSpecial &7tag for our'
      - '&7early supporters!'
    slot: 9
    priority: 18
    view_requirement:
      requirements:
        joinlate:
          type: javascript
          expression: '%javascript_epoch_time% > 1632913200000'
```


It's a pretty basic script, but using epoch was the easiest way to make a value that can be applied in a boolean statement.
