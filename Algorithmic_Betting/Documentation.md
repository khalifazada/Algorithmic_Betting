
Algorithmic Betting
===

### Quick Introduction
: This document serves the purpose of being a comprehensive documentation explaining in greater and extensive detail a systematic placement of football game bets according to some chosen strategy. It accompanies the *Games Data.xlsx* file explaining how to work with it.

We start with derivations of certain properties and build extensively on that. So without further ado here's an example:

FC Barcelona vs Atletico Madrid is on and we decide to place bets in such manner that we reduce risk. Barcelona being arguably stronger than Atletico is our $1st$ choice. In addition to that we place a $2nd$ bet on a *draw* scenario. Let $x$ be the bet we place on Barcelona at decimal odds $b_1$ and let $y$ be the bet we place on draw at odds $b_2$. We want to place such $x$ and $y$ so that regardless of the outcome of the above events our win amount is exactly the same. This means that $x$ and $y$ must not be equal if $b_1\neq b_2$. More on this below. The implied odds $b_1, b_2$ are quoted by all major bookmakers and brokers. Thus, we define $$T=x+y$$ where $T$ is the total amount we want to risk, and equality  $$xb_1=b_2y$$ follows since we need our win to be equal regardless of the outcome. 

	Example:
		b_1=1.50		b_2=4.00
		x=$72.73		y=$27.27
		
		T=x+y=$100.00
		
		b_1*x=$109.09
		b_2*y=$109.09

In the above example it doesn't matter if Barcelona wins or both draw our win will be the same. We only loose all of $T$ if *Atletico* wins since we havent placed any bets on this outcome (i.e. $z=0$.) Further I will talk about how to calculate at which $b_3$ what amount of $z$ to bet in order to be able to precisely calculate and control the amount of capital to recover. 
	Our goal now is to find what $x, y$ are equal to. We observe that $xb_1=b_2(T-x)$ from the above equality and $x(b_1+b_2)=b_2T$.

Thus,
$$x=T\frac {b_2}{b_1+b_2},	y=T\frac {b_1}{b_1+b_2}$$

Notice that we are free to choose $T$ in any way we please. It is simply the amount of money that we are willing to bet. For the sake of simplicity I'm a proponent of choosing $T=\$1.00$ then $x,y < 1$ and now everything can be expressed in decimals to be easily interpreted as % if necessary.
___
### Growth

The entire strategy is constructed around the behavior of a single formula shown below.

### $$G={(R_s^{F_s}R_f^{F_f})}^n$$

$G$ is an index that represents growth. When $G=1$ it shows that no growth has occurred. $G<1$ means there was a loss. Essentially it is just a product of all wins and losses. 

	Example:
	Sequence of results from placing bets represented as % growth:
	1.06*1.11*0.97*1.34=1.53

The above sequence of $4$ bets results in overall $53\%$ increase. So, the $1st$ game resulted in $6\%$ increase, $2nd$ game was even more and $3rd$ game was a $3\%$ loss. Notice how we record a loss.

For simplicity of calculation suppose we observe a sequence $W_1W_2W_3L_1L_2$ where each win and loss is $15\%$. Numerically this is what we observe:
$$1.15*1.15*1.15*0.85*0.85$$
which can we rewritten as $1.15^30.85^2$. 

So if $R_s$, $R_f$ represent geometric averages of all succeeded and failed games respectively. The above formula originally looked like this:

$$G=R_s^{nF_s}R_f^{nF_f}$$

because if we define $W$ as alland may appear a bit more interpretative perhaps if we call $nF_s$ and $nF_f$ total number of wins and losses respectfully.

	Example:
		nF_s=3 wins
		nF_f=1 loss
		
		R_s=1.09
		R_f=0.85
		
		G=1.09^3*0.85=1.10
To understand $nF_{s,f}$ we define $n$ as the total number of games played and $F_{s,f}$ as the proportions of those games being successes and failures respectfully. In the above example $n=4, F_s=\frac 34, F_f=\frac 14$
We will construct our strategy in such a way that when *Atletico* wins and thus $3rd$ outcome occurs we recover some back at the end of the game preventing total loss.

Here's a different example with $n=365$ representing $1$ game per day for $1$ year.

	Example:
	n=365
	F_s=0.75
	F_f=0.25

	R_s=1.09
	R_f=0.85
		
	G=(1.09^0.75*0.85^0.25)^365=6,382.35

In the above example playing at a rate of $1$ game per day and winning $75\%$ of games each at $9\%$ while loosing $15\%$ per game $25\%$ of the time results in $638,235\%$ growth.

Staggering, yes! But not so fast.
___

### Proportions

Proportions are simply ratios of failures $p$ (or successes $q$) to total number of games $n=p+q$.

### $$F_s=\frac q{p+q}, F_f=\frac p{p+q}$$

	Example:
		p=173
		q=94
		
		n=173+94=267
		F_f=173/267=0.6579
		F_s=94/267=0.3521


Technically $F_f$ is simply $F_f=1-F_s$

### Geometric Averages



### $$R_f={\prod_{i=0}^p {R_{f_i}}}^{\frac 1p} \text {}, R_s={\prod_{i=0}^q {R_{s_i}}}^{\frac 1q} \text {}$$

### Recovery Bet

Recovery bet is placed at a pre-calculated $b_3$ when the opposing team scores and $3rd$ outcome occurs

$$b_3=\frac {W_E}{B(1-R_{f_i})-\frac {B}{\sigma}+W_E}$$

Before we derive the above formula we need to define certain concepts and understand where they come from. Notice that after each game the new balance of the account is simply $B-L+W$, where $B$ is last balance, $L$ are the losses and $W$ is the amount won. $L$ itself is simply $L=x+y+z$ since that is the amount of money that leaves the account. $W_E$ is *expected* win hence the ${}_E$ subscript. So expressed as $\%$ our account looks like this:

$$\frac {B-L+W_E}{B}$$

This is where we can take control over how much we wish to loose and let's say we decide to place a recovery bet when our losses reach $37\%$ for this game making $R_{f_i}=1-0.37=0.63$ for this particular game.

Thus, if $3rd$ event happens, *Atletico* scores, our team starts to loose. We want to place a recovery bet at such point that will guarantee $63\%$ recovery of the account before the game is over. In other words we want:

$$\frac {B-L+W_E}{B}=R_{f_i}$$

Read further to understand how all of this blends together into the above formula.

Second, we take a closer look at $L$. We now add $z$ into the equality and notice that

$$W_E:=xb_1=yb_2=zb_3$$

Notice also that every bet can be defined as:

$$x=\frac {W_E}{b_1}, y=\frac {W_E}{b_2}, z=\frac {W_E}{b_3}$$

We make all of these substitutions and get:

$$\frac {B-(\frac {W_E}{b_1}+\frac {W_E}{b_2}+\frac {W_E}{b_3})+W_E}{B}=R_{f_i}$$

Before we do any further re-arrangements of terms let's introduce another concept of *initial* balance control. Assume you split your account in half before you place bets and always use only $50\%$ of $B$ to come up with $T$. Remember that it was $T=x+y$. Basically $T=\frac B2$ or in general 

$$T=x+y=\frac B\sigma$$

if we want to define some $\sigma$ to represent a fraction of our account.
Again, putting all of the above together we get:

$$\frac {B-(\frac {W_E}{b_3}+\frac B\sigma)+W_E}{B}=R_{f_i}$$

$$B(1-R_{f_i})-\frac B\sigma+W_E=\frac {W_E}{b_3}$$

and finally we get

$$b_3=\frac {W_E}{B(1-R_{f_i})-\frac {B}{\sigma}+W_E}$$


In summary, if we placed bets $x,y$ before the start of the game and if at some point our team starts to loose we simply wait until odds for the opponent team decay to $b_3$ and place a recovery bet $z$.

To correctly find $b_3$ we just need to know how much we want to recover and how much we want to win. The latter directly depends on bets we placed before the game started whilst the former is completely arbitrary in terms of choice. This arbitrariness and freedom of choice of value for $R_{f_i}$ gives us  the ability to set particular targets as will be explored later.

	Example:
		B=$300.00
		R_f_i=0.55
		sig=2
		W_E=$50.00

		b_3=50/(300*(1-0.55)-(300/2)+50)=1.43

		z=50/1.43=$34.97

In the above example we would be required to place a bet of $z=\$34.97$ when odds are $b_3=1.43$ to recover $55\%$ of our account. Keeping everything else the same, if we would like to recover $80\%$ of our account then we would have to place a bet of $$ $$
___

##Money Management System

> Based on extended Martingale betting system

### $$G=1+\frac {L+W}{T}$$

where,

$L=(n+2)-2^{n+1}$ and represents losses suffered at $nth$ step of a sequence of trades. Notice $L<0$ is always true.

	Example:
	We suffered 3 consecutive losses:
	n=3
	L=(-1)+(-3)+(-7)=(3+2)-2^(3+1)=-11

$W=2^{m}-1$ is win on $mth$ step which is always the last one in the sequence of trades. $W \gt 0$

	Example:
	Our 4th trade was a win:
	m=4
	W=2^4-1=15

In the above two examples having enough capital to open 4 trades requires having at least $T$ amount in value. So before placing trades we need to have $26=1+3+7+15$ units. We allocate unitary value for the $1st$ trade and lose it.

$$1st\rightarrow-1$$

$$2nd\rightarrow-3$$

$$3rd\rightarrow-7$$

$$4th\rightarrow+15$$

$T=2^{N+1}-(N+2)$, where $N$ is the total number of consecutive losses that we are able/willing to sustain and $T$ is the total number of units we need to have on our balance to do that.  

Continuing the above example we were willing to sustain 4 consecutive losses and a sequence of $4$ trades resulted in $3$ losses and $1$ win and brought:

$$G=1+\frac{[2^{3+1}-(3+2)]+[2^4-1]}{2^{4+1}-(4+2)}=1+\frac {[-11]+[15]}{26}=115\%$$

In addition to the above calculation suppose the proportion of consecutive losses happens with following frequencies:

|$0th$	|$1st$	|$2nd$	|$3rd$	|$4th$	|
|:------|:------|:------|:------|:------|
|19		|6		|3		|1		|0		|

So we observe $19$ events where 

$$0 \le n \lt N$$

$$0 \le m \le N$$


$K=\{3, 8, 3\}, k_i \in K, i \in I$
$n=\{0, 1, 2\}$
$N=4, $

$$G_i=\prod_{i=1}^{|K|} {[1+\frac {((n_i+2)-2^{n_i+1})+(2^{m_i+1}-1)}{2^{N+1}-(N+2)}]}^{k_i}$$

	Example:
	N=4, n_i=0, m_i=0, 
> Written with [StackEdit](https://stackedit.io/)