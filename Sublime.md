# Sublime教程

## 安装Package Control
- view->Show Console
```
import  urllib.request,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();urllib.request.install_opener(urllib.request.build_opener(urllib.request.ProxyHandler()));open(os.path.join(ipp,pf),'wb').write(urllib.request.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())
```

## 安装Markdown
- Install MarkdownEditing

## 安装Git
- 安装Git软件，默认下一步即可
- 安装Package插件: Git