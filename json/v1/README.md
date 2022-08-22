# JSON v1

## Overview
```ts
{
    version: string
    $static: {
      color: TokenInfo,
      dimension: TokenInfo,
      'font-weight': TokenInfo,
      'line-height': TokenInfo,
      'letter-spacing': TokenInfo,
    },
    $scale: {
      color: TokenInfo,
      dimension: TokenInfo,
      'font-weight': TokenInfo,
      'line-height': TokenInfo,
      'letter-spacing': TokenInfo,
    },
    $semantic: {
      color: TokenInfo,
      dimension: TokenInfo,
      'font-weight': TokenInfo,
      'line-height': TokenInfo,
      'letter-spacing': TokenInfo,
      typography: CompositeTokenInfo,
    },
}
```

## TokenInfo

```ts
interface TokenInfo {
  name: string;
  description: string;
  values: Record<string, string>;
}
```

### 테마에 따라 값이 달라지는 토큰
```json
{
    "name": "gray-00",
    "description": "",
    "values": {
        "theme-light": "#ffffff",
        "theme-dark": "#17171a"
    }
}
```

### 테마에 관계없이 값이 일정한 토큰
```json
{
    "name": "static-black",
    "description": "",
    "values": {
        "*": "#000000"
    }
}
```

### 다른 토큰을 참조하는 토큰
```json
{
    "name": "primary",
    "description": "",
    "values": {
        "theme-light": "$scale.color.carrot-500",
        "theme-dark": "$scale.color.carrot-500"
    }
}
```

## CompositeTokenInfo

```ts
interface CompositeTokenInfo {
  name: string;
  description: string;
  properties: Record<string, Record<string, string>>;
}```
```

```json
"caption2-bold": {
    "name": "caption2-bold",
    "description": "",
    "properties": {
        "font-size": {
            "*": "$scale.dimension.font-size-50"
        },
        "font-weight": {
            "*": "$static.font-weight.bold"
        },
        "line-height": {
            "*": "$static.line-height.static-small"
        },
        "letter-spacing": {
            "platform-ios": "$scale.letter-spacing.none",
            "platform-android": "$scale.letter-spacing.narrow-400"
        }
    }
}
```