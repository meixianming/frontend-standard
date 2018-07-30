# 前端开发代码规范

## 一、javascript

代码美化

工具： [Prettier](https://www.npmjs.com/package/prettier)


```js
{
    //一行代码显示的最多打印的字符数
	"printWidth": 120,
    //是否使用tab代替space
	"useTabs": true,
    //tab操作对应的space数
	"tabWidth": 4,
    //是否打印分号
	"semi": true,
    //字符串是否使用单引号：否; 当前标准：全部统一采取双引号方式
	"singleQuote": false,
    //是否在文件头中插入美化指示命令 @prettier, 当前标准: 文件默认开启
	"requirePragma": false,
    //是否在美化后的文件中插入美化指示命令，否；
	"insertPragma": false,
    //是否需要尾逗号： 不需要;
	"trailingComma": "none",
	//括号之间的打印space: 是的;
    "bracketSpacing": true,
    //箭头函数的参数周围是否用圆括号包含: 是；即使是单个参数也要包含，方便语义化
	"arrowParens": "always",
    //从当前文件的哪个位置开始执行美化，0 代表文件头
	"rangeStart": 0,
    //针对jsx语法的是否是在行结束的时候打印">"符号
	"jsxBracketSameLine": false,
	"proseWrap": "preserve",
	"parser": "babylon"
}
```

代码语法验证:

工具: [ESLint](http://eslint.cn/)

与变量相关的验证规则:

```js
{
    //禁止删除变量,delete操作只限定去用在删除对象属性上,不能做变量删除;
    "no-delete-var": "error",
    //不允许标签与变量同名
    "no-label-var":"error",
    //禁止将标识符定义为受限的名字,例如 var Undefined , var NaN , function NaN()等
    "no-shadow-restricted-names":"error",
    //禁用未声明的变量
    "no-undef":"error",
    //禁止初始化变量值为 undefined,由于声明了的变量系统会自动赋予undefined的值
    "no-undef-init":"error",
    //不允许使用undefined变量
    "no-undefined":"error",
    //禁止未使用过的变量
    "no-unused-vars": ["error", { "vars": "all", "args": "none", "ignoreRestSiblings": true }],
    //禁止变量在定义前使用,例如: alert(a); var a = 1;
    "no-use-before-define": ["error", { "functions": false, "classes": false, "variables": false }]
}
```

与CommonJS规范编写代码时的验证规则:

```js
{
    //要求回调函数中有容错处理
	"handle-callback-err": ["error", "^(err|error)$"],
	//禁止调用 require 时使用 new 操作符
	"no-new-require":"error",
    //禁止对 __dirname 和 __filename 进行字符串连接
    "no-path-concat":"error",
    //禁用 process.exit()，此操作会中断整个进程
    "no-process-exit":"warn"
}
```

使用ES6标准编写代码时的验证规则:

```js
{
	//要求箭头函数的参数使用圆括号, 例如 x=>... 中的 x必须使用()包装 即: (x)=>...
	"arrow-parens":"error"
    //强制箭头函数的箭头前后使用一致的空格,要求前后都需要
    "arrow-spacing": ["error", { "before": true, "after": true }],
	//要求在构造函数中有 super() 的调用
	"constructor-super":"error"
	//强制 generator 函数中 * 号周围使用一致的空格,要求前后都需要
	"generator-star-spacing":["error", { "before": true, "after": true }],
	//禁止修改类声明的变量
	"no-class-assign":"error",
	//禁止修改 const 声明的变量
	"no-const-assign":"error",
	//禁止类成员中出现重复的名称
	"no-dupe-class-members":"error",
	//禁止重复模块导入
	"no-duplicate-imports":"error",
	//禁止 Symbolnew 操作符和 new 一起使用
	"no-new-symbol":"error",
	//禁止使用指定的 import 加载的模块,这个验证规则需要根据项目来进行实际的配置，目前暂时关闭状态
	"no-restricted-imports":"off",
	//禁止在构造函数中，在调用 super() 之前使用 this 或 super
	"no-this-before-super":"error",
	//禁止在对象中使用不必要的计算属性,例如 var f={[`a`]:"b}, 常量非计算的属性无需使用计算属性特性来操作
	"no-useless-computed-key":"error",
	//禁用不必要的构造函数
	"no-useless-constructor":"error"
	//禁止在 import 和 export 和解构赋值时将引用重命名为相同的名字,即import出来的变量重命名时与原包名变量命名相同，此操作完全多次一举
	"no-useless-rename":"error",
	//要求使用 let 或 const 而不是 var
	"no-var":"error",
	//要求或禁止对象字面量中方法和属性使用简写语法
	"object-shorthand":"error",
	//要求回调函数使用箭头函数
	"prefer-arrow-callback":"error",
	//要求使用 const 声明那些声明后不再被修改的变量
	"prefer-const":"error",
	//要求使用剩余参数而不是 arguments
	"prefer-rest-params":"error",
	//要求使用扩展运算符而非 .apply()
	"prefer-spread":"warn"
	//要求 generator 函数内有 yield
	"require-yield":"warn",
	//强制剩余和扩展运算符及其表达式之间绝对不能有空格
	"rest-spread-spacing":["error","never"],
	//强制模块内的 import 排序
	"sort-imports": ["error", {
        "ignoreCase": true,
        "ignoreMemberSort": false,
        "memberSyntaxSortOrder": ["single", "all", "multiple", "none"]
    }],
	//要求 symbol 描述
	"symbol-description": "error",
	//禁止模板字符串中的嵌入表达式周围空格的使用
	"template-curly-spacing":["error","never"],
	//强制在 yield* 表达式中 * 周围使用空格
	"yield-star-spacing": ["error", "both"]
}
```

代码编写过程中容易造成逻辑错误的规则:

```js
{
	//禁止与 -0 进行比较    	
	"no-compare-neg-zero":"error",
	//禁止条件表达式中出现赋值操作符
    "no-cond-assign":"warn",
    //禁用 console
    "no-console":"warn",
    //禁止在条件中使用常量表达式,但允许在循环中使用常量表达式
    "no-constant-condition":["error",{checkLoops:false}],
    //禁止在正则表达式中使用控制字符
    "no-control-regex":"error",
    //禁止出现debugger
    "no-debugger":"error",
    //禁止 function 定义中出现重名参数
    "no-dupe-args":"error",
    //禁止对象字面量中出现重复的 key
    "no-dupe-keys":"error",
    //禁止出现重复的 case 标签
    "no-duplicate-case":"error",
    //禁止出现空语句块
    "no-empty":"error",
    //禁止在正则表达式中使用空字符集
    "no-empty-character-class":"error",
    //禁止对 catch 子句的参数重新赋值
    "no-ex-assign":"error",
    //禁止不必要的布尔转换
    "no-extra-boolean-cast":"error",
    //禁止不必要的括号
    "no-extra-parens":["error","functions"],
    //禁止不必要的分号
    "no-extra-semi":"error",
    //禁止对 function 声明重新赋值
    "no-func-assign":"error",
    //禁止在嵌套的块中出现变量声明或 function 声明
	"no-inner-declarations": ["error", "functions"],
	//禁止 RegExp 构造函数中存在无效的正则表达式字符串
    "no-invalid-regexp":"error",
    //禁止在字符串和注释之外不规则的空白
    "no-irregular-whitespace":["error",{"skipComments": true}],
    //禁止把全局对象作为函数调用
	"no-obj-calls":"error",
	//禁止正则表达式字面量中出现多个空格
	"no-regex-spaces":"error",
	//禁用稀疏数组
  	"no-sparse-arrays":"error",
    //禁止在常规字符串中出现模板字面量占位符语法
    "no-template-curly-in-string":"error",
    //禁止出现令人困惑的多行表达式
    "no-unexpected-multiline":"error",
    //禁止在return、throw、continue 和 break 语句之后出现不可达代码
    "no-unreachable":"error",
    //禁止在 finally 语句块中出现控制流语句
	"no-unsafe-finally":"error"，
    //禁止对关系运算符的左操作数使用否定操作符
	"no-unsafe-negation":"error",
    //要求使用 isNaN() 检查 NaN
    "use-isnan":"error",
    //强制 typeof 表达式与有效的字符串进行比较
   	"valid-typeof": ["error", { "requireStringLiterals": true }]
}
```

ESLint统计出来的一些最佳实践中的规则:

```js
{
    //强制 getter 和 setter 在对象中成对出现
    "accessor-pairs":"error",
    //强制数组方法的回调函数中有 return 语句
    "array-callback-return":"off",
    //强制把变量的使用限制在其定义的作用域范围内
    "block-scoped-var":"warn",
    //指定程序中允许的最大环路复杂度
    "complexity":["error",4],
    //强制所有控制语句使用一致的括号风格
	"curly": ["error", "multi-line"],
    //要求 switch 语句中有 default 分支
    "default-case":"warn"
    //强制在点号之前和之后一致的换行
    "dot-location": ["error", "property"],
    //强制尽可能地使用点号
    "dot-notation":"warn",
    
    //要求使用 === 和 !== , null值的比对可以忽略
    "eqeqeq": ["error", "always", { "null": "ignore" }],
    //禁用 arguments.caller 或 arguments.callee
    "no-caller":"error",
    //禁止 if 语句中 return 语句之后有 else 块
    "no-else-return":"warn",
    //禁止出现空函数
    "no-empty-function": ["error", { "allow": ["functions", "constructors"] }],
    //禁止使用空解构模式
    "no-empty-pattern":"error",
    //禁止在没有类型检查操作符的情况下与 null 进行比较
    "no-eq-null":"error",
    //禁用 eval()
    "no-eval":"error",
    //禁止扩展原生类型
    "no-extend-native":"error",
    //禁止不必要的 .bind() 调用
    "no-extra-bind":"error",
    //禁止 case 语句落空
    "no-fallthrough":"error",
    //禁止数字字面量中使用前导和末尾小数点
    "no-floating-decimal":"error",
    //禁止对原生对象或只读的全局对象进行赋值
    "no-global-assign":"error",
    //禁止使用短符号进行类型转换
    "no-implicit-coercion":"off",
    //禁止使用类似 eval() 的方法
    "no-implied-eval":"error",
    //禁用 __iterator__ 属性
    "no-iterator":"error",
    //禁用标签语句
    "no-labels": ["error", { "allowLoop": false, "allowSwitch": false }],
    //禁用不必要的嵌套块
    "no-lone-blocks":"error",
    //禁止在循环中出现 function 声明和表达式
    "no-loop-func":"error",
    //禁止使用多个空格
    "no-multi-spaces":"error",
    //禁止使用多行字符串
    "no-multi-str":"error",
    //禁止使用 new 以避免产生副作用
    "no-new":"error",
    //禁止对 Function 对象使用 new 操作符
    "no-new-func":"error",
    //禁止对 String，Number 和 Boolean 使用 new 操作符
    "no-new-wrappers":"error",
    //禁用 __proto__ 属性
    "no-proto":"error",
    //禁止多次声明同一变量
    "no-redeclare":"error",
    //警告: 在 return 语句中使用赋值语句,除了箭头函数中的
    "no-return-assign": ["warn", "except-parens"],
    //禁用不必要的 return await
    "no-return-await":"error",
    //禁止自我赋值
    "no-self-assign":"error",
    //禁止自身比较
    "no-self-compare":"error",
    //禁用逗号操作符
    "no-sequences":"error",
    //禁止抛出异常字面量
    "no-throw-literal":"error",
    //禁用一成不变的循环条件
    "no-unmodified-loop-condition":"error",
    //禁止出现未使用过的表达式
	"no-unused-expressions": [
        "error",
        { "allowShortCircuit": true, "allowTernary": true, "allowTaggedTemplates": true }
    ],
    //禁用出现未使用过的标
    "no-unused-labels":"",
    //禁止不必要的 .call() 和 .apply()
    "no-useless-call":"error",
    //禁用不必要的转义字符
    "no-useless-escape":"error",
    //禁止多余的 return 语句
    "no-useless-return":"error",
    //禁用 with 语句
    "no-with":"error",
    //要求使用 Error 对象作为 Promise 拒绝的原因
    "prefer-promise-reject-errors":"error",
    //强制在parseInt()使用基数参数
    "radix":"error",
    //禁止使用不带 await 表达式的 async 函数
    "require-await":"error",
    //要求 IIFE 使用括号括起来
    "wrap-iife": ["error", "any", { "functionPrototypeMethods": true }],
    //要求或禁止 “Yoda” 条件
    "yoda":["error", "never"]
}
```

ESLint提出的针对用户的主观性代码风格配置(个人调整后)

```js
{
    
    //在数组开括号后和闭括号前强制换行
    "array-bracket-newline": ["error", { "multiline": true, "minItems": 4 }],
    //强制数组方括号中使用一致的空格
    "array-bracket-spacing":["error","always"],
    //禁止或强制在代码块中开括号前和闭括号后有空格
    "block-spacing":["error","always"],
    //强制在代码块中使用一致的大括号风格
	"brace-style": ["error", "1tbs", { "allowSingleLine": true }],
    //强制使用骆驼拼写法命名约定
    "camelcase":["error", { "properties": "never" }],
    //要求或禁止末尾逗号
    "comma-dangle": [
        "error",
        {
            "arrays": "never",
            "objects": "never",
            "imports": "never",
            "exports": "never",
            "functions": "never"
        }
    ],
    //强制在逗号前后使用一致的空格
    "comma-spacing": ["error", { "before": false, "after": true }]
    //强制使用一致的逗号风格
    "comma-style":["error", "last"],
    //强制在计算的属性的方括号中使用一致的空格
    "computed-property-spacing":["error","always"],
    //当获取当前执行环境的上下文时，强制使用一致的命名 self
    "consistent-this":["error","self"],
    //要求或禁止文件末尾存在空行
    "eol-last":"error",
    //要求或禁止在函数标识符和其调用之间有空格
    "func-call-spacing":["error","never"],
    //强制在函数括号内使用一致的换行
    "function-paren-newline": ["error", { "minItems": 4 }],
    //强制使用一致的缩进
    "indent": [
        "error",
        "tab",
        {
            "SwitchCase": 1,
            "VariableDeclarator": 1,
            "outerIIFEBody": 1,
            "MemberExpression": 1,
            "FunctionDeclaration": { "parameters": 1, "body": 1 },
            "FunctionExpression": { "parameters": 1, "body": 1 },
            "CallExpression": { "arguments": 1 },
            "ArrayExpression": 1,
            "ObjectExpression": 1,
            "ImportDeclaration": 1,
            "flatTernaryExpressions": false,
            "ignoreComments": false
        }
    ],
    //强制在 JSX 属性中一致地使用双引号或单引号
    "jsx-quotes":["error","prefer-double"],
    //强制在对象字面量的属性中键和值之间使用一致的间距
    "key-spacing": ["error", { "beforeColon": false, "afterColon": true }],
    //强制在关键字前后使用一致的空格
    "keyword-spacing": ["error", { "before": true, "after": true }],
    //强制使用一致的换行风格 \n
    "linebreak-style": ["error", "unix"],
    //要求或禁止在三元操作数中间换行
    "multiline-ternary":"off",
    //要求构造函数首字母大写
    "new-cap": ["error", { "newIsCap": true, "capIsNew": false }],
    //要求调用无参构造函数时有圆括号
    "new-parens":"error",
    //要求方法链中每个调用都有一个换行符
    "newline-per-chained-call":"",
    //禁用 Array 构造函数
    "no-array-constructor":"error",
    //禁用按位运算符
    "no-bitwise":"off",
    //禁用 continue 语句
    "no-continue":"off",
    //禁止混合使用不同的操作符
    "no-mixed-operators": [
        "error",
        {
            "groups": [["==", "!=", "===", "!==", ">", ">=", "<", "<="], ["&&", "||"], ["in", "instanceof"]],
            "allowSamePrecedence": true
        }
    ],
    //禁止空格和 tab 的混合缩进
    "no-mixed-spaces-and-tabs":"error",
    //禁止出现多行空行
    "no-multiple-empty-lines": ["error", { "max": 1, "maxEOF": 0 }],
    //禁用 tab,必须使用
    "no-tabs":"off",
    //禁用行尾空格
    "no-trailing-spaces":"error",
    //禁止可以在有更简单的可替代的表达式时使用三元操作符
   	"no-unneeded-ternary": ["error", { "defaultAssignment": false }],
    //禁止属性前有空白
    "no-whitespace-before-property":"error",
    //强制将对象的属性放在不同的行上
	"object-property-newline": ["error", { "allowMultiplePropertiesPerLine": true }],
    //强制函数中的变量要么一起声明要么分开声明
    "one-var": ["error", { "initialized": "never" }],
    //强制操作符使用一致的换行符
    "operator-linebreak": ["error", "after", { "overrides": { "?": "before", ":": "before" } }],
    //要求或禁止块内填充
    "padded-blocks": ["error", { "blocks": "never", "switches": "never", "classes": "never" }],
    //强制使用一致的反勾号、双引号或单引号
	"quotes": ["error", "double", { "avoidEscape": true, "allowTemplateLiterals": true }],
    //要求或禁止使用分号代替 ASI
    "semi": ["error", "always"],
    //强制分号之前和之后使用一致的空格
    "semi-spacing": ["error", { "before": false, "after": true }],
    //要求对象属性按序排列
    "sort-keys": ["error", "asc", {"caseSensitive": false, "natural": true}],
    //要求同一个声明块中的变量按顺序排列
    "sort-vars": ["error", {"ignoreCase": true}],
    //强制在块之前使用一致的空格
    "space-before-blocks": ["error", "always"],
    //强制在 function的左括号之前使用一致的空格
    "space-before-function-paren": [
        "error",
        {
            "anonymous": "always",
            "named": "never",
            "asyncArrow": "always"
        }
    ],
    //强制在圆括号内使用一致的空格
    "space-in-parens": ["error", "never"],
    //要求操作符周围有空格
    "space-infix-ops": "error",
    //强制在一元操作符前后使用一致的空格
    "space-unary-ops": ["error", { "words": true, "nonwords": false }],
    //强制在注释中 // 或 /* 使用一致的空格
    "spaced-comment": [
        "error",
        "always",
        {
            "line": { "markers": ["*package", "!", "/", ",", "="] },
            "block": {
                "balanced": true,
                "markers": ["*package", "!", ",", ":", "::", "flow-include"],
                "exceptions": ["*"]
            }
        }
    ],
    //强制在 switch 的冒号左右有空格
    "switch-colon-spacing": ["error", {"after": true, "before": false}],
    //要求或禁止在模板标记和它们的字面量之间有空格
    "template-tag-spacing": ["error", "never"],
    //要求或禁止 Unicode 字节顺序标记 (BOM)
    "unicode-bom": ["error", "never"]
}
```
## 二、CSS / LESS / SASS

工具: [StyleLint](https://stylelint.io)

格式验证和美化规则: 

```json
{
    //禁止无效十六进制颜色
    "color-no-invalid-hex": [
        true,
        {
            "message":"无效的十六进制颜色"
        }
     ],
    //不允许重复的字体名称
    "font-family-no-duplicate-names": [
        true,
        {
            "message": "不允许出现重复的字体名称"
        }
    ],
    "at-rule-empty-line-before": [
        "always",
        {
            "except": ["blockless-after-same-name-blockless", "first-nested"],
            "ignore": ["after-comment"],
              "message": "在样式规则之前要求空行,在注释后面的除外"
        }
    ],
    "at-rule-name-case": [
        "lower",
        {
            "message":"样式规则的名称只能是小写"
        }
    ],
    "at-rule-name-space-after": [
        "always-single-line",
        {
            "message":"单行声明的规则名称之后必须是单个space"
        }
    ],
    "at-rule-semicolon-newline-after": [
        "always",
        {
            "message":"样式规则名称的分号后面总是需要换行"
        }
    ],
    "block-closing-brace-empty-line-before": [
        "never",
        {
            "message":"样式规则块闭合之前不需要空行"
        }  
     ],
    "block-closing-brace-newline-after":  [
        "always",
        {
            "message":"在关闭块后需要一个换行符或不允许的空白"
        }  
     ],
    "block-closing-brace-newline-before":"always-multi-line",
    "block-closing-brace-space-before": "always-single-line",
    "block-opening-brace-newline-after": "always-multi-line",
    "block-opening-brace-space-after": "always-single-line",
    "block-opening-brace-space-before": "always",
    "color-hex-case": [
        "lower",
        {
            "message":"十六进制颜色必须小写"
        }
     ],
    "color-hex-length": [
        "short",
        {
            "message":"十六进制颜色使用短符号格式"
        }
    ],
    "comment-empty-line-before": [
        "always",
        {
            "except": ["first-nested"],
            "ignore": ["stylelint-commands"]
        }
    ],
    "comment-whitespace-inside": "always",
    "custom-property-empty-line-before": [
        "always",
        {
            "except": ["after-custom-property", "first-nested"],
            "ignore": ["after-comment", "inside-single-line-block"]
        }
    ],
    "declaration-bang-space-after": "never",
    "declaration-bang-space-before": "always",
    "declaration-block-semicolon-newline-after": "always-multi-line",
    "declaration-block-semicolon-space-after": "always-single-line",
    "declaration-block-semicolon-space-before": "never",
    "declaration-block-single-line-max-declarations": 1,
    "declaration-block-trailing-semicolon": "always",
    "declaration-colon-newline-after": "always-multi-line",
    "declaration-colon-space-after": "always-single-line",
    "declaration-colon-space-before": "never",
    "declaration-empty-line-before": [
        "always",
        {
            "except": ["after-declaration", "first-nested"],
            "ignore": ["after-comment", "inside-single-line-block"]
        }
    ],
    "function-comma-newline-after": "always-multi-line",
    "function-comma-space-after": "always-single-line",
    "function-comma-space-before": "never",
    "function-max-empty-lines": 0,
    "function-name-case": "lower",
    "function-parentheses-newline-inside": "always-multi-line",
    "function-parentheses-space-inside": "never-single-line",
    "function-whitespace-after": "always",
    "indentation": "tab",
    "length-zero-no-unit": true,
    "max-empty-lines": 1,
    "media-feature-colon-space-after": "always",
    "media-feature-colon-space-before": "never",
    "media-feature-name-case": "lower",
    "media-feature-parentheses-space-inside": "never",
    "media-feature-range-operator-space-after": "always",
    "media-feature-range-operator-space-before": "always",
    "media-query-list-comma-newline-after": "always-multi-line",
    "media-query-list-comma-space-after": "always-single-line",
    "media-query-list-comma-space-before": "never",
    "no-eol-whitespace": true,
    "no-missing-end-of-source-newline": true,
    "number-leading-zero": "always",
    "number-no-trailing-zeros": true,
    "property-case": "lower",
    "rule-empty-line-before": [
        "always-multi-line",
        {
            "except": ["first-nested"],
            "ignore": ["after-comment"]
        }
    ],
    "selector-attribute-brackets-space-inside": "never",
    "selector-attribute-operator-space-after": "never",
    "selector-attribute-operator-space-before": "never",
    "selector-combinator-space-after": "always",
    "selector-combinator-space-before": "always",
    "selector-descendant-combinator-no-non-space": true,
    "selector-list-comma-newline-after": "always",
    "selector-list-comma-space-before": "never",
    "selector-max-empty-lines": 0,
    "selector-pseudo-class-case": "lower",
    "selector-pseudo-class-parentheses-space-inside": "never",
    "selector-pseudo-element-case": "lower",
    "selector-pseudo-element-colon-notation": "double",
    "selector-type-case": "lower",
    "unit-case": [
        "lower",
        {
            "except": ["Px", "px"],
              "message":"除了Px以及px之后的单位都必须小写"
        }
    ],
    "value-list-comma-newline-after": "always-multi-line",
    "value-list-comma-space-after": "always-single-line",
    "value-list-comma-space-before": "never",
    "value-list-max-empty-lines": 0
}
```



为了统一整个协同工作环境下的css样式便于review，通过第三方辅助工具 stylelint-order去执行样式的排序 , 相关配置内容如下:

```json
{
    "order/order": ["custom-properties", "declarations"],
    "order/properties-alphabetical-order": true
}
```


## 三、VUE

1. 项目目录结构规范

   ```
   |--- build									// 项目打包相关配置，基于webpack
   	|--- utils.js			
   	|--- vue-loader.conf.js					  // webpack针对.vue文件的配置options
   	|--- webpack.base.conf.js				  // webpack针对当前项目的基础配置
   	|--- webpack.dev.conf.js				  // webpack针对开发环境的配置
   	|--- webpack.dll.conf.js				  // webpack针对公共包的提取配置
   	|--- webpack.prod.conf.js				  // webpack针对生成环境的配置
   |--- dist									// 打包后的目标文件夹
   |--- src									// 源码目录
   	|--- apis								// 请求后端数据Api的封装目录
   	|--- assets								// 资源文件目录
   		|--- imgs							// 图片
   		|--- less/scss/stylus				 // 预编译css文件目录
   		|--- fonts							// 字体文件目录
   		|--- icons							// 图标文件目录
   		|--- medias							// 媒体文件目录
   	|--- components							// 当前项目自定义组件文件目录
   	|--- directives							// vue组件开发相关指令代码目录
   	|--- filters							// vue组件开发相关过滤器代码目录
   	|--- mixins								// vue组件开发相关混合器代码目录
   	|--- routes								// 项目路由配置目录
   	|--- stores								// 项目数据统一管理目录
   	|--- utils								// 辅助方法代码目录
   	|--- views								// 项目视图目录
   	|--- App.vue							// 项目启动的母版页
   	|--- main.js							// 项目代码的入口文件
   |--- static									// 第三方静态文件目录
   |--- .babelrc								// babel-loader使用的babel ES6转ES5代码的配置文件
   |--- .eslintrc.json							 // eslint代码验证的规则配置文件
   |--- .gitignore								 // git提交时需忽略的文件清单配置
   |--- .postcssrc.js							 // postcss相关配置
   |--- .prettierignore						 // prettier美化代码格式所需忽略的文件清单配置
   |--- .prettierrc.json						 // prettier美化代码规则配置
   |--- .stylelintrc.json						 // 样式文件的格式和编码规则配置
   |--- package.json							 // 项目的工程配置文件

   ```

2. 单vue文件开发规范

   1) 顺序性: style > template > script

   ```vue
   <style>
   ....
   </style>

   <template>
   ...
   </template>

   <script>
   ...
   </script>
   ```

   2) vue组件命名规范

   * 小写
   * 简短: 一般不大于3个单词
   * 使用连字符分隔单词
   * xx公共库组件： "xx-"开头
   * 业务项目专属组件:  项目名称拼音前两个单词首字母+'-' ,例如资讯 'zx-'

   ```
   <!------ 推荐 ------>
   <!-- 公共库 -->
   <xx-input></xx-input>
   <xx-button></xx-button>

   <!-- 特定业务组件 -->
   <zx-news-item></zx-news-item>
   ```

   3) vue内部挂在方法放置顺序

   ```js
   export default {
       name:"组件名称",
       <!-- 组件关系 --->
       components:{}, //子组件填充
       <!--- 属性类操作 --->
       props:"组件对外的属性定义",
       data:"组件内部消费的成员属性集合",
       computed:"计算属性",
       watch:"属性监听",
       filter:"属性过滤",
       <!-- 方法类操作 --->
       mixins:[], //当前组件所需的混合器
       methods:"所有当前组件的实例方法",
       <!-- 生命周期类 --->
       beforeCreated:
       created:
       beforeMounted:
       mounted:
       activated:
       beforeUpdate:
     	updated:
       beforeDestory:
       destroyed:
   }
   ```

   4) vue `data`属性的命名规范

   * 所有属性以驼峰命名标准
   * Boolean类型的属性，必须使用`is`开头,例如 `isShow`,`isCancel`

   ​


    5) vue `methods`命名规范

    * 驼峰命名
    * 动宾短语
    * $emit出去的方法名称格式: "on-`操作名称`", `操作名称`使用连字符分隔;
    * 关联其他组件$emit的方法名称: "handle"+上述`操作名称`的驼峰格式
    * 事件类的方法全部以 `on`开头 
    * 内部辅助方法作为私有方法的全部以"__"开头

   ```vue
   <template>
   	<div>
           <other-component @on-item-click="handleItemClick"></other-component>
       </div>
   </template>
   <script>
   export default{
       name:"zs-news-item",
       methods:{
           <!-- 私有方法-->
           __convertData(){},
           <!-- 驼峰命名、动宾短语-->
           getData(){},
       	<!-- 事件方法 -->
           onClick(event){
       		<!-- $emit出去的方法名称格式 -->
   			this.$emit("on-item-click",event);
           }，
       	<!-- 关联其他组件$emit的方法名称 -->
           handleItemClick(){}
       }
   }
   </script>
   ```

3. Vue项目Views文件夹内单Vue文件的命名:

   * 驼峰命名,但首字母大写
   * 页面模式: 新增(CreateXXX.vue)、修改(UpdateXXX.vue)、删除(DeleteXXX.vue)、详情(XXXDetail.vue)

## 四、开发工具

 推荐使用 [visual studio code](https://code.visualstudio.com/)

* 工具使用前准备:

先安装[node.js](https://nodejs.org/en/),安装完成之后执行如下命令验证是否安装成功


> node -v //输出 `v8.11.1`
> npm -v //输出 `5.6.0`

设置npm的远程镜像源为国内快速源


> npm set registry https://registry.npm.taobao.org/

全局安装工具包yarn、eslint、stylelint

>  npm i -g yarn eslint stylelint

检测yarn是否安装成功

> yarn -v //输出`1.5.1`

* 插件安装: visual studio code安装成功之后,安装以下插件辅助开发过程中的代码格式控制
  * [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
  * [stylelint](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint)
  * [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  * [vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
* 工作区配置 : 每个前端项目在创建的时候会在每个项目的vscode的相关工作区中添加如下设置:

```json
{
    "editor.tabSize": 4,
    
    //vetur格式化单vue文件中的<template>内容的格式器
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    
    //关闭默认的css验证
    "css.validate":false,
    //关闭默认的less验证
    "less.validate":false,
    //关闭默认的scss验证
    "scss.validate":false,
	
    "[vue]":{
        "formatOnSave":true
    },
    "[json]": {
    	"editor.formatOnSave": true
    },
    "[css]": {
    	"editor.formatOnSave": true
    },
    "[less]": {
    	"editor.formatOnSave": true
    },
    "[scss]": {
    	"editor.formatOnSave": true
    },
    "[html]": {
    	"editor.formatOnSave": true
    },
    
    //设置eslint在每个保存的时候主动执行--fix操作将代码统一
    "eslint.autoFixOnSave": true,
    //开启eslint的文件类型
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "html",
        "vue",
        {
            "language": "vue",
            "autoFix": true
        },
        {
        "language": "html",
        "autoFix": true
        }
    ],
    
    //将prettier与eslint配合开启
    "prettier.eslintIntegration": true,
    //将prettier与stylelint配合开启
    "prettier.stylelintIntegration": true,
    //prettier忽略的文件配置
    "prettier.ignorePath": ".prettierignore",
	
    //开启stylelint
    "stylelint.enable": true
}
```

