注意，本文章均为虚构，不影射任何现实人物，如有雷同纯属巧合。

点击链接查看 oierdb 奖项信息：<https://oier.baoshuo.dev/oier/169157>

![](https://cdn.luogu.com.cn/upload/image_hosting/qus0euet.png)

嗟夫！夫以坚韧之志，凌寒暑而不辍；以颖悟之资，贯艰深而愈进。然时运起伏，竟如潮汐；得失错迕，恍若参商。岂其智有不逮耶？抑天之磨砺英才，必先戏其心志乎？然观其啜汤饭以自警，处低谷而愈奋，则来日之腾骧，或未可量也。时人录其行迹，非独述奇，亦以见竞赛之道甘苦相杂，而志士之心，终不蒙尘矣。

### 一些有趣的事实

1. 周佳润同学在 2022-06-25 注册了自己的洛谷账号：[zhoujiarun](https://www.luogu.com.cn/user/741775)，采用的实名上网的策略沿用到了 2025-04-23 洛谷用户名被强制更改，头像采用为洛谷默认头像，到 2025-04-23 被强制更改为另一个默认头像。

2. [zhoujiarun](https://www.luogu.com.cn/user/741775) 在 2022-06-25 20:15 [提交](https://www.luogu.com.cn/record/77900905) 并一遍通过了自己的**第一道**题目 [P 1909 [NOIP 2016 普及组] 买铅笔](https://www.luogu.com.cn/problem/P1909)，并且代码由自己手写完成：

```cpp
#include<iostream>
using namespace std;

int main(){
	int p,a,b,c,x,y,z;
	cin>>p>>a>>x>>b>>y>>c>>z;
	int m=((p-1)/a+1)*x;
	int n=((p-1)/b+1)*y;
	int o=((p-1)/c+1)*z;
	int minn=m;
	if(minn>n){
		minn=n;
	}
	if(minn>o){
		minn=o;
	}
	cout<<minn;
	return 0;
}
```

3. [zhoujiarun](https://www.luogu.com.cn/user/741775) 在 2024-12-19 15:18 [提交](https://www.luogu.com.cn/record/195138619) 并通过了自己的**最后一道**题目 [
AT_agc 034_d [AGC 034 D] Manhattan Max Matching](https://www.luogu.com.cn/problem/AT_agc034_d)，很遗憾，这是一篇[题解](https://www.luogu.com.cn/article/hpk2n1d2)。

```cpp
#include<bits/stdc++.h>
#define maxn 1010
#define inf 1000000007
using namespace std;
typedef long long ll;
int read()
{
    int x=0,f=1;
    char ch=getchar();
    while(ch-'0'<0||ch-'0'>9){if(ch=='-') f=-1;ch=getchar();}
    while(ch-'0'>=0&&ch-'0'<=9){x=x*10+ch-'0';ch=getchar();}
    return x*f;
}
int n,p1,p2,p3,p4,s,t;
int head[maxn*2],nxt[maxn*20],to[maxn*20],c[maxn*20],v[maxn*20],tot=1;
void add(int x,int y,int z,int u)
{
    ++tot;
    nxt[tot]=head[x];
    head[x]=tot;
    to[tot]=y;
    c[tot]=z;
    v[tot]=u;
}
void addx(int x,int y,int z,int u)
{
    add(x,y,z,u);
    add(y,x,0,-u);
}
ll ans;
ll dis[maxn*2];
int pre[maxn*2],pre_num[maxn*2],vis[maxn*2];
queue<int>q;
int spfa()
{
    for(int i=1;i<=t;i++)  dis[i]=-1e16;
    q.push(s);dis[s]=0;vis[s]=1;
    while(q.size())
    {
        int now=q.front();q.pop();vis[now]=0;
        for(int i=head[now];i;i=nxt[i])
        {
            if(dis[to[i]]<dis[now]+v[i]&&c[i])
            {
                dis[to[i]]=dis[now]+v[i];
                pre[to[i]]=now;
                pre_num[to[i]]=i;
                if(!vis[to[i]])  q.push(to[i]),vis[to[i]]=1;
            }
        }
    }
    if(dis[t]==-1e16)  return 0;
    int di=inf;
    for(int i=t;i!=s;i=pre[i])  di=min(di,c[pre_num[i]]);
    for(int i=t;i!=s;i=pre[i])  c[pre_num[i]]-=di,c[pre_num[i]^1]+=di;
    ans+=dis[t]*di;
    return di;
}
int main()
{
    n=read();p1=2*n+1;p2=p1+1;p3=p2+1;p4=p3+1;s=p4+1;t=s+1;
    for(int i=1;i<=n;i++)
    {
        int x=read(),y=read(),z=read();
        addx(s,i,z,0);
        addx(i,p1,inf,x+y);
        addx(i,p2,inf,x-y);
        addx(i,p3,inf,-x+y);
        addx(i,p4,inf,-x-y);
    }
    for(int i=1;i<=n;i++)
    {
        int x=read(),y=read(),z=read();
        addx(i+n,t,z,0);
        addx(p1,i+n,inf,-x-y);
        addx(p2,i+n,inf,-x+y);
        addx(p3,i+n,inf,x-y);
        addx(p4,i+n,inf,x+y);
    }
    while(spfa()){};
    printf("%lld\n",ans);
    return 0;
}
```

4. 上面的两个事实全部是错误的，实际上，[zhoujiarun](https://www.luogu.com.cn/user/741775) 现在没有通过任意一道题目。

5. [zhoujiarun](https://www.luogu.com.cn/user/741775) 直到自己退役都没有注册过任意一个 cf 或 at 或者 uoj 等其它 oj 的账号，他所使用的 oj 仅有洛谷一个。

6. [zhoujiarun](https://www.luogu.com.cn/user/741775) 所有 ccf 正式比赛的挂分 $^{[1]}$ 是全机房无可争议的最高峰，共有 csp-j 2023 的 185 pts，csp-s 2023 的 5 pts，snoi 2024 的 300 pts，csp-s 2024 的 90 pts，总计 580 pts。幸运的是，他的 noip 2024、snoi 2025 得分和自己的预估完全一致。

7. [zhoujiarun](https://www.luogu.com.cn/user/741775) 在退役之前每天进行 6:30-22:30 长达 16 个小时的 oi 训练，这让他达成了在均匀写蓝紫的情况下 8 天完成了 100 道洛谷紫题，1.5 个月完成了 400 道洛谷紫题的历史性成就。

![](https://cdn.luogu.com.cn/upload/image_hosting/g78e3mmh.png)

8. 不幸的是，2025 年 4 月，chen_zhe 注意到了这个账号并且永久清空了这个账号的所有做题记录。让我们为机房传奇 zhoujiarun 悼观 1 分钟。

![](https://cdn.luogu.com.cn/upload/image_hosting/hx0yj327.png)

9. 由于 zhoujiarun 是一个诚实的人，所以他的游戏账号全部采用自己本人的实名信息，即使这会导致防沉迷。于是 zhoujiarun 计算了三天三夜，终于得出了如何充值原神月卡能获得最大收益 $^{[2]}$！从此他每周末 19：30 准时离开机房回家，再到 21：30 回到机房 $^{[3]}$。

### Zhoujiarun 的 oi 历程

周佳润同学在 2022-06-25 注册了自己的洛谷账号：[zhoujiarun](https://www.luogu.com.cn/user/741775)，开始了自己长达 908 天、21787 个小时、1307223 分钟的 oi 生涯。根据某些推测，[zhoujiarun](https://www.luogu.com.cn/user/741775) 在 2023 年 4 月由初二班主任代洁玲推荐找到了 xgdfz 机房，并且勤勤恳恳开始在机房和校外机构一起上课并且疯狂做题。这使得他的水平得到了极大的提升，并且在 csp-j 2023 获得了 115 pts，csp-s 2023 获得了 95 pts。

但是他并没有因此气馁，在 2023 年 12 月选择了停课训练。在此之后，他终于开启了自己的传奇 oi 生涯之路。停课训练最初，[zhoujiarun](https://www.luogu.com.cn/user/741775) 是唯一能够在模拟赛中稳定打出极高分并且持续领跑全机房的人，并且他的模拟赛极高的得分持续到了退役前一天，这一点在之后会有详细的解释。[zhoujiarun](https://www.luogu.com.cn/user/741775) 与常人不同的是，他不屑于使用自带的笔记本，而是坚持使用学校 win 7 后来升级为 win 11 又换机房降级到 win 7 的电脑，这种艰苦的精神也值得我们学习。

2024 年 1 月，勰码冬令营在 xgdfz 举办，不同于其它初三根本听不懂于是开始放飞自我划水的人，[zhoujiarun](https://www.luogu.com.cn/user/741775) 认真听完了所有的课程，并且依旧坚持 7 点到校十点半离校的规律作息，在此之间，他学习了网络流、平衡树、SAM、PAM 等等一系列高难度的算法并且通过了超过 100 道网络流题目。勰码营结束后，同届同学向 zhoujiarun 提出质疑，认为他的网络流题目全部都是照抄的题解。Zhoujiarun 超级生气暴怒开始争论，但在对方提出比一下随机跳一道流题看谁做的快后拒绝并迅速回家。

2 月份教练查看所有人的做题记录，[zhoujiarun](https://www.luogu.com.cn/user/741775) 以超过同届其他所有人蓝紫黑数目的总和的做题量震惊了全机房，教练对他寄予厚望，认为他就是继上一块 au pyf 之后有望拿到 au 的下一个人。一些证据表明，zhoujiarun 的 100 道网络流题目模板几乎从不复制全部重写，但是 100 道的模板几乎互不相同，具体取决于题目的题解，例如加/不加当前弧优化，建图用 vector/链式前向星，当然 vector 不多，因为大部分题解不会用 vector 写 dinic。

3 月 snoi 2024 举行，zhoujiarun 直接强势通过 d 1 t 1，d 1 t 3，d 2 t 1，这次他做到了，不止于同届选手，整个机房上到进入省队的高二学生，下到初二的小朋友全部拜倒在 zhoujiarun 的强大实力之下。不过后来查分，zhoujiarun 的成绩 $^{[4]}$ <= 20。不过他并未在意，继续保持着稳定的模拟赛 rk 1，无论是在老机子还是新机子，无论是有网还是断网，他都有自己的应对方法。Zhoujiarun 在当月中旬随大家一起搬到了新机房，但是依然不使用自己的笔记本，所以电脑可惜降级到了 win 7，不过他没有任何怨言，依然勤勤恳恳的做题。

4 月 xgdfz 实行了竞赛班政策，zhoujiarun 再次轻松进入竞赛班并以近乎场场 ak 的水平领跑机房 noip 模拟赛，无论模拟赛难度有多大，zhoujiarun 总能轻松的获得至少 2 道正解和 2 道极高非平凡部分分的成绩，这让大家对他的 csp 2024、noip 2024 寄予厚望。竞赛班规划是每天早上学文化课，下午学竞赛，我选择了全停，因为我认为竞赛班文化课没什么意思。但是我们 zhoujiarun 不乐意了，凭什么我要学文化课，而你能停课？于是和父母在家大打出手，不过双拳难敌四手落败。Zhoujiarun 父亲想到了完美的方案：如同疯狗一般联系我的原班主任、我的竞赛班班主任、机房竞赛教练和我的家长，质问我为什么停课，他们家孩子怎么办？蛊惑我的家长，虽然高中已经决定直接录取，但是你的孩子中考考不好，初中知识没学会，将来高中怎么办？马上就要成为 oi 失利文化课完蛋的路边废物了。而我的孩子学习初中文化课，将来就算 oi 爆炸也能随便碾压高考轻松上清北。于是我被迫继续和 zhoujiarun 大神成为同学，早上在竞赛班教室睡觉。

5 月 zhoujiarun 临近中考，选择全部放弃 oi 而进行中考复习，同时让他的父亲继续发挥特长，劝说同届的所有家长，让他们所有人来陪自己一起全天学文化课。文化课的学习无疑也是 zhoujiarun 的强项，他上课时从不睡觉，并且以政治见长，政治例析与指导上密密麻麻都是他的笔记，已经做好了万全的准备来应对中考。在此期间，他终于抽到了自己最长时间未复刻的女神优菈。

6 月初竞赛班举行联欢晚会来庆祝解散，zhoujiarun 很快就远离了班级，因为嘈杂的环境影响了他的学习。停课复习，与前 200 在实验楼打原神的我不同，zhoujiarun 依然在废寝忘食的学习，手提一个手提袋来学校，熟练的打开需要复习的书，并且以极高的频率前去请教老师们。Zhoujiarun 在中考考场门口使用他爹的手机玩《崩坏：星穹铁道》，这表明他对中考十分自信。果不其然，我在考完和他进行了政治科目的交流，一个高达 8 分的大题我询问他如何作答，他显示出极高兴的神色，手舞足蹈的向我阐释了他的答案如何构成：抄写了哪本书的资料 $^{[5]}$、哪个老师讲过的必须要答的点、哪些他偶然间想得但极为契合的点等等等等，看起来他已经开启了香槟，对自己的成绩报有极大的信心。

7 月份 zhoujiarun 听取教练的要求前往绍兴一中外培。在前去的火车上大家要么在拿电脑打游戏，要么在打牌。而 zhoujiarun 静静坐在一旁看着旁人的嬉戏，自己则是打开桌子研读教练推荐的《母函数》。但是绍一的模拟赛大多为学生自己出的或者搬的模拟赛新题，zhoujiarun 的成绩瞬间跌入谷底，例如声称自己完成了线性代码但是 1 e 5 要跑 480 s、挂分远大于得分等等一系列悲情失误。在回到宿舍后，与打 kirka 的同学不同，他总是打开自己的手机，默默的观看《原神》4.8 夏活剧情，然后在十点钟准时躺下睡觉，毫不拖沓一分。中考成绩出了，与 zhoujiarun 良好的预期不同，他无比自傲的政治获得了 **70** 分，甚至比天天睡大觉政治书全是空白的我还要低 7 分。这一如同母亲死去 $^{[6]}$ 的巨大的打击使 zhoujiarun 陷入了无比的自责当中，当天午饭为了警示自己，他只选用了免费的米饭和汤并就着解决了自己的午餐。这种头悬梁锥刺骨的精神无不鼓舞着我们。

8 月份回来之后机房掀起了 tetr 之风，zhoujiarun 在一边警示自己的中考成绩从而疯狂训练 oi 之外，利用闲暇时间体验了 tetr，并用别人的真实姓名注册了帐号之后，以 0.3 pieces per second 的块速吊打了全机房加冕为 tetr 之神。也就是在这时，他做到了曾经的梦想，在 2024-08-24 这天，他产生了高达 3 页的提交记录并且通过了 30 道题。$^{[7]}$ 这说明他已经具备了约 25.6667 $^{[8]}$ 分钟解决一道紫题的能力！这已经达到了大部分集训队的水平，也许已经超过了。他的洛谷做题记录几乎每天都是相差不多的黑色长条，最高的一天更是高达 40 道题，不过由于暑假有约 100 页的提交记录，我懒得去寻找具体是哪一天了。

9 月份高中开学，zhoujiarun 正式成为了一名高中的学生。按照一贯的传统，大家会先前往高中自己的班级上 1-2 周再停课训练准备 csp。在这一段时间过后，zhoujiarun 毅然决然的选择停课，但是他的父母对此不太同意。于是 zhoujiarun 又思考了三天三夜，将他的父母斩于马下之后成功获得了停课训练 oi 的机会。为了不辜负自己努力争取来的停课名额，zhoujiarun 立即停止了一切暑假时还会有的颓废的活动开始认真训练，例如 b 站、tetr、mc 等等等等。

这时候机房的模拟赛频率非常高，大概每天都有一场，zhoujiarun 的成绩依然非常的好。比方说一次互测，我写了 3 h 多才过了一个搬的计数 dp t 4，但 zhoujiarun 与我们这些平凡的 oi 选手不同，他打开了神秘网站 $^{[9]}$ 并只用了 5 min 通过这道题，成为了唯二通过的人。不过我和 zhoujiarun 的区别在于，他顺手通过了除了 t 2 之外的所有题并且提前离场，但我整场只写了 t 4 一个题。至于为什么没有通过 t 2？因为当时的 ai 并不发达，加以 t 2 是一道原创题。Csps 2024 初赛也在这几天，不过 zhoujiarun 考了多少分我忘了，不过可以确认的是 <= 70。我至今都扼腕于 zhoujiarun 生在了一个 ai 并不发达的时代，否则他的 cf 或者 at rating 应当轻松匹敌当今世界上最强的 ai。

10 月份国庆假期，zhoujiarun 休息了 0 天而训练了超过 100 个小时 oi。家中父母的反抗越来越大，但看在他训练如此认真，也只能忍痛继续任由他停课。马上就是 csp 2024 了，zhoujiarun 开启了更为疯狂的训练，誓要在这场比赛证明自己的水平。10 月 26 日，csp 2024 如期举行，zhoujiarun 于中午到达了长安大学考点，和中考一样抢夺他爹的手机游玩《崩坏：星穹铁道》并且成为全场第一个进入考场的人

### Zhoujiarun oi 生活的一天

### 注释

$[1]$：这里挂分指预估得分和实际得分之差。
$[2]$：周内无法上线无法领取 90 原石。
$[3]$：防沉迷可游玩时间段为周五到周日的 20：00 - 21：00。
$[4]$：第一天与第二天的成绩之和。
$[5]$：SN 政治中考为开卷考试。
$[6]$：zhoujiarun 的母亲其实并未去世。
$[7]$：这只是随机选取了暑假的某一天进行的统计，并不是 zhoujiarun 的暑假最高峰。
$[8]$：$770 / 30 \approx 25.6667$。
$[9]$：指 `yuantiji.ac`。
### 参考文献

我的大脑记忆。