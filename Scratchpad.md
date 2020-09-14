postman
milkman
air hostess
housewife
taxi driver
hairdresser
mechanic
policeman
policewomen
nurse

Countries:

- Chinese
- American
- French
- German
- Swedish
- Korean
- English
- Italian
- increment
- decrement

TODO:

vim:

- [ ] return position, after alt_shift_j or alt_shift_k

## make table in markdown

- replace the `|<space>` at start of line, `'<,'>s/\v^\| /|:/`
- replace the `<space>|` at start of line, `'<,'>s/\v \|$/:|/`
- replace all characters which are not, `:` or `|`: `'<,'>s/[^:\|]/-/g`

Months of year

- January
- February
- March
- April
- May
- June
- July
- August
- September
- October
- November
- December

sheetAPI:

- [x] 获取表格元数据
- [ ] 更新表格属性
- [ ] 操作子表更新子表属性
- [x] 插入数据
- [x] 追加数据
- [x] 插入行列
- [x] 增加行列
- [x] 更新行列
- [x] 删除行列
- [ ] 设置单元格样式
- [ ] 批量设置单元格样式
- [ ] 增加锁定单元格
- [ ] 合并单元格
- [ ] 拆分单元格
- [x] 读取单个范围
- [x] 向单个范围写入数据
- [x] 读取多个范围
- [x] 向多个范围写入数据

"snippets.snipmate.enabled": true,
"snippets.ultisnips.pytthonVersion": 3

export PASSWD49="Sinopharm@wms_159"

rsync -a --rsh='sshpass -e ssh -l root' 192.168.70.49:/root/virusLog_wmsmscnew ./includes/

rsync --rsh='sshpass -e ssh -l root' ./checklogs.sh 192.168.70.49:/root

scp root@192.168.70.6:/root/virusLog/ ./includes/

# meta template {{{

snippet meta "asciidoc meta header" b
= \${1:`!p snip.rv = snip.basename or "untitled"`}
gk07 <gk_520@hotmail.com>
\${2:v1.0}, `!v strftime("%Y-%m-%d")`
:toc:
:icons: font
:library: Asciidoctor
// ifdef::asciidoctor[]
// :source-highlighter: coderay
// endif::asciidoctor[]
:idprefix:
// :stylesheet: ../../resources/asciidoctor.css
:imagesdir: images
:includesdir: includes
//:title-logo-image: image:logo.png[pdfwidth=3.00in,align=center]
//:backend: docbook45
//:backend: html5
//:doctype: book
//:sectids!:
:plus: &#43;

// refs
:url-github: https://github.com/Kunkgg
//:url-blog: http-to-my-blog

endsnippet

# }}} meta template
