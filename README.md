# config for apps

## Clash

此配置是为了建立虚拟网卡，实现真正的全局代理。

[教程-Youtube](https://www.youtube.com/watch?v=eOG6YJjSyak&t=547s&ab_channel=%E7%A7%91%E6%8A%80%E5%88%86%E4%BA%AB)

在配置文件的末尾加上这么一段代码，即可启用虚拟网卡。

```yaml
dns:
  enable: true
  enhanced-mode: redir-host # 或 fake-ip
  listen: 0.0.0.0:53
  nameserver:
    - 223.5.5.5
```

## Karabiner

目的是将方向键映射到其他键位上。

[教程-CSDN](https://blog.csdn.net/xjc2998310890/article/details/116356978)

我又改了一点：

- `caps` + `h`: `cmd` + `left_arrow`，跳转到行首
- `caps` + `u`: `opt` + `left_arrow`，左走一个单词
- `caps` + `;`: `cmd` + `right_arrow`，跳转到行末
- `caps` + `o`: `opt` + `right_arrow`，右走一个单词

json文件如下

```json
{
  "title": "`Use CAPS LOCK for vi navigation",
  "rules": [{
      "description": "CAPS LOCK + jkliuoh to arrow keys",
      "manipulators": [{
          "type": "basic",
          "from": {
            "key_code": "k",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "down_arrow"
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        }, {
          "type": "basic",
          "from": {
            "key_code": "i",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "up_arrow"
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        }, {
          "type": "basic",
          "from": {
            "key_code": "j",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "left_arrow"
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        }, {
          "type": "basic",
          "from": {
            "key_code": "l",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "right_arrow"
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        },{
          "type": "basic",
          "from": {
            "key_code": "u",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "a",
            "modifiers": ["left_control"]
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        },{
          "type": "basic",
          "from": {
            "key_code": "o",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "e",
	    "modifiers": ["left_control"]
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        },{
          "type": "basic",
          "from": {
            "key_code": "h",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "key_code": "delete_or_backspace"
          }],
          "conditions": [{
            "type": "variable_if",
            "name": "caps_lock pressed",
            "value": 1
          }]
        },
        {
          "type": "basic",
          "from": {
            "key_code": "caps_lock",
            "modifiers": {
              "optional": [
                "any"
              ]
            }
          },
          "to": [{
            "set_variable": {
              "name": "caps_lock pressed",
              "value": 1
            }
          }],
          "to_after_key_up": [{
            "set_variable": {
              "name": "caps_lock pressed",
              "value": 0
            }
          }]
 
      }]
}]
}
```
