记录主题配置
# ========== Profile ========== #
# avatar
avatar: /avatar/Misaka.jpg
# author name
author: Mer
# signature
signature: 
# SNS (you can custom the order)
social:
  email: 
  github: 
  # wechat and qq should be a path of qr-code image
  wechat:
  qq: 
  telegram: 
  weibo: 
  zhihu: 
  douban: 
  facebook: 
  twitter: 
  instagram: 
  stack-overflow: 
  segmentFault: 
  juejin: 
  v2ex: 
  bilibili: 
  linkedin: 
  steam: 
  others: 
  rss: 
sharewrapper: false
# friends
friends:
  maqun: https://www.marke.xin/
  friendB: 
  friendC: 
about:
  enable: false
  image: '/intro/about-bg.jpg'

# ========== Site ========== #
# title of the site (good for SEO)
SEO_title: Mer blod
# keywords for site (good for SEO)
SEO_keywords:
  - mer
  - 'hexo-theme'
  - 'hexo-blog'
# main title shown in header image
main_title: Mer blod
# subtitle
subtitle: 书山有路勤为径，学海无涯苦作舟
# site haeder image
site_header_image: '/intro/index-bg.jpg'
# post haeder image
post_header_image: '/intro/post-bg.jpg'
# 404 image
_404_image: '/intro/404-bg.jpg'

# ========== Search ========== #
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We did not find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# ========== Comment ========== #
# Fill in the field to enable the corresponding comment plugin
# If you want to add other comment plugin, edit in "custom.ejs"
comment:
  # Livere  site: https://livere.com/
  livere_uid: 
  # Disqus  site: https://disqus.com/
  disqus_shortname: 
  # Gitment  site: https://github.com/imsun/gitment
  gitment_owner: 
  gitment_repo: 
  gitment_client_id: 
  gitment_client_secret: 
  # Youyan  site: http://www.uyan.cc/
  youyan_uid: 
  # Valine  site: https://valine.js.org/
  valine_appId: 
  valine_appKey: 
  valine_placeHolder: 

# ========== Analytics ========== #
# enable Busuanzi analytics
busuanzi: false
# fill in pv or uv
busuanzi_pv_or_uv: 'pv'
# custom analytic slogan, '${count}' is the analytic number, DO NOT modify it.
busuanzi_slug: 'PV: ${count} :)'
# Baidu analytics
baidu_analytics: 
# Google analytics
google_analytics: 
# CNZZ analytics
CNZZ_analytics: 

# ========== Others ========== #
# favicon
favicon: /assets/favicon.ico
# truncate length of abstracts in index page (the default is 300, there will be no abstruct if you input 0)
truncate_length: 
# enable toc
toc: true
# word count & reading time
reading_info: true
# intro height (the default is 50 percents of the screen, you can input other number)
index_intro_height: 50
post_intro_height: 50
about_intro_height: 50
# copyright
copyright:
  enable: false
  # https://creativecommons.org/
  license: '本文采用<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">知识共享署名-非商业性使用 4.0 国际许可协议</a>进行许可'
