---
title: Fuwari blog 導航欄新增連結
published: 2025-03-25
description: "AULyPc大佬+我的修改建議(?"
tags: ["web"]
category: meow
draft: true
lang: zh_TW
---
:::caution
這篇是參考[AULyPc - 给你的Fuwari添加一个友链页面](https://blog.aulypc0x0.online/posts/add_friendspage_in_fuwari/)，再加入我的一點改善作法
:::


如圖所示，原始的Fuwari blog導航欄只有一點東西，雖然作者沒有提供較方便的方式新增欄位，但我們可以透過自己修改與新增部分內容已達成目的
![image](https://hackmd.io/_uploads/SJzqNpgTyl.png)

或許這就是open source的魅力吧(笑
<!-- 接下來我會參考AULyPc大佬的做法及我的建議-->

# 新增欄位

這邊就假設新的欄位名稱叫"Meow"

- 在`\src\content\spec`新增`meow.md`
- 在`src\types\config.ts`，第37行`export enum LinkPreset`加入`Friends`
 ```ts
 export enum LinkPreset {
  Home = 0,
  Archive = 1,
  About = 2,
  Meow = 3,
}
```
- 在`src\i18n\i18nKey.ts`大約第6行加入`meow = 'meow'`
```ts
enum I18nKey {
  home = 'home',
  about = 'about',
  archive = 'archive',
  search = 'search',
  meow = 'meow',
  //以下略
}
export default I18nKey

```
- 在`src\i18n\languages\<你的語言>.ts`約第9行加入`[Key.meow]: 'Meow',`(這邊以`en.ts`為例)
```ts
export const en: Translation = {
  [Key.home]: 'Home',
  [Key.about]: 'About',
  [Key.archive]: 'Archive',
  [Key.search]: 'Search',
  [Key.meow]: 'Meow',
  //以下略
}
```
- 在`src\constants\link-presets.ts`中添加內容
```ts
import { LinkPreset, type NavBarLink } from '@/types/config'
import I18nKey from '@i18n/i18nKey'
import { i18n } from '@i18n/translation'

export const LinkPresets: { [key in LinkPreset]: NavBarLink } = {
    //略
    [LinkPreset.Meow]: {
    name:i18n(I18nKey.meow),
    url: '/meow/',
  },
}
```
- 在`src\pages\`下，複製`about.astro`，並命名為`meow.astro`
在第10,12,14行，把`about`修改為`meow`
```astro
const aboutPost = await getEntry('spec', 'about')

const { Content } = await aboutPost.render()
---
<MainGridLayout title={i18n(I18nKey.about)} description={i18n(I18nKey.about)}>
```
(節錄)
- 最後在`src\config.ts`大約第45行處加入`LinkPreset.Meow,`
```ts
export const navBarConfig: NavBarConfig = {
  links: [
    LinkPreset.Home,
    LinkPreset.Archive,
    LinkPreset.About,
    LinkPreset.Meow,
    // {
    //   name: 'GitHub',
    //   url: 'https://github.com/saicaca/fuwari',     // Internal links should not include the base path, as it is automatically added
    //   external: true,                               // Show an external link icon and will open in a new tab
    // },
  ],
}
```

# 添加卡片

最一般的方法，是在`<div class="card-base z-10 px-9 py-6 relative w-full ">`內部加入以下內容:

```ts
<div class="grid grid-cols-1 sm:grid-cols-2 gap-x-6 gap-y-8 my-4">
    {items.map((item) => (
        <div class="flex flex-nowrap items-stretch h-28 gap-4 rounded-[var(--radius-large)]">
            <div class="w-28 h-28 flex-shrink-0 rounded-lg overflow-hidden bg-zinc-200 dark:bg-zinc-900">
                <img src={item.imgurl} alt="站点头像" class="w-full h-full object-cover">
            </div>
            <div class="grow w-full">
                <div class="font-bold transition text-lg text-neutral-900 dark:text-neutral-100 mb-1">{item.title}</div>
                <div class="text-50 text-sm font-medium">{item.desc}</div>
                <div class:list={["items-center", {"flex": true, "hidden md:flex" : false}]}>
                    <div class="flex flex-row flex-nowrap items-center">
                        {(item.tags && item.tags.length > 0) && item.tags.map((tag,i) => (
                            <div class:list={[{"hidden": i==0}, "mx-1.5 text-[var(--meta-divider)] text-sm" ]}>
                                /
                            </div>
                            <span class="transition text-50 text-sm font-medium">
                        {tag}
                    </span>))}
                        {!(item.tags && item.tags.length > 0) && <div class="transition text-50 text-sm font-medium">{i18n(I18nKey.noTags)}</div>}
                    </div>
                </div>
            </div>
            <a href={item.siteurl} target="_blank" rel="noopener noreferrer"class="flex btn-regular w-[3.25rem] rounded-lg bg-[var(--enter-btn-bg)] hover:bg-[var(--enter-btn-bg-hover)] active:bg-[var(--enter-btn-bg-active)] active:scale-95">
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" class="transition text-[var(--primary)] text-4xl mx-auto iconify iconify--material-symbols" width="1em" height="1em" viewBox="0 0 24 24">
                    <path fill="currentColor" d="M12.6 12L8.7 8.1q-.275-.275-.275-.7t.275-.7t.7-.275t.7.275l4.6 4.6q.15.15.213.325t.062.375t-.062.375t-.213.325l-4.6 4.6q-.275.275-.7.275t-.7-.275t-.275-.7t.275-.7z"></path>
                </svg>
            </a>
        </div>
    ))}
</div>
```
並且在`---`前加入:
```astro
const items = [
  {  
    title: 'Astro',  
    imgurl: 'https://avatars.githubusercontent.com/u/44914786?s=48&v=4',  
    desc: 'The web framework for content-driven websites. ⭐️ Star to support our work!',  
    siteurl: 'https://github.com/withastro/astro',  
    tags: ['框架'],  
  },
]
```
> 如果有問題，歡迎去看看[我的GitHub](https://github.com/cxk228922/robin-tw/blob/main/src/pages/meow.astro)
> 
以上是AULyPc大老的作法，但這樣會造成一點小問題，卡片資訊無法放在別的文本中間

因為一般Astro的md只會輸出Content的Component，如果使用以下方法(簡)就會出錯
```astro
const meowPost = await getEntry('spec', 'meow')
const meowEnd = await getEntry('spec', 'meow-end')

const { Content } = await meowPost.render()
const { ContentEnd } = await meowEnd.render()
<Markdown class="mt-2">
    <Content />
</Markdown>
//上部的md內容            
<div class="grid grid-cols-1 sm:grid-cols-2 gap-x-6 gap-y-8 my-4">
//略
</div>
<Markdown class="mt-2">
    <ContentEnd />
</Markdown>
//下部的md內容
```
我的解決方法是改成
```astro
const { Content: IntroContent } = await meowPost.render()
const { Content: EndContent } = await meowEnd.render()

<Markdown class="mt-2">
    <IntroContent />
</Markdown>
<div class="grid grid-cols-1 sm:grid-cols-2 gap-x-6 gap-y-8 my-4">
//略
</div>
<Markdown class="mt-2">
    <EndContent />
</Markdown>
```

以上，如有問題歡迎DM我!