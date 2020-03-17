---
title: 마법공식(Joel Greenblatt)
tags: Finance
aside:
  toc: true
---

# Remarks
이 글은 [자본수익률과 이익수익률 산출 및 적용](http://www.selffund.co.kr/magicstock/magicstock_04.asp)의 내용을 정리한 글입니다.

<!--more-->

---

## 1. 자본수익률(資本收益率)과 이익수익률(利益收益率) 산출의 필요성
상위 종목을 선택하는 방식으로 **일반적인 선별방법(이하 일반법)**와 **원론적 방법론(이하 원론법)**를 사용한다.
- **일반적인 선별방법: PER + ROA**
- **원론적 방법론: 자본수익률 + 이익수익률**

일반법은 원론법에 비해 자료 산출 방식이 상대적으로 간단하지만 전문성을 가지고 장기간에 걸쳐 투자를 진행하기에는 미흡한 부분이 있어 보완이 필요한 방법이다. 이에 따라, 원론법의 정확한 정의와 장점을 파악하고 실제 투자에 적용하는 방법에 대해 설명하려 한다.


## 2. 일반적 선별 방식의 보완 필요성과 개선점
원론법과 비교하여 일반법의 보완해야할 부분부터 살펴보자.  

1. 각각 **자본수익률(ROC)**과 **이익수익률**을 치환하는 **ROA**와 **PER**의 지수 값들이 해당 기업의 **세전 영업이익(EBIT)**이 아닌 일률적인 **당기 순이익**으로 측정되기 때문에 각 기업이 가지고 있는 영업력을 동등한 조건하에서 비교하지 못하는 문제점이 있다.

2. ROA의 서로 다른 수준의 세율과 부채에서 비롯되는 왜곡 뿐만 아니라 공시된 자기 자본 및 자산과 유형자기자본 및 자산 사이의 차이를 무시함으로써 생기는 자본수익률의 왜곡이 가장 대표적인 문제점이다.


## 3. 자본수익률의 구성요소

**자본수익률(資本收益率, ROC, Return On Capital)**
어떤 기업의 개설비용 대비 투자수익률의 기댓값  
$ROC = \frac{EBIT}{투입유형자본} = \frac{EBIT}{순운전자본 + 순고정자산}$
{:.success}
  
- **EBIT(Earnings Before Interast and Taxes, 이자 및 법인세 공제 전 영업이익)**  
일반적으로 EBIT는 우리나라 회계기준에서는 명확히 정의할 수 없는 다분히 미국적 회계기준에 준한 계정(計定)이다.  
EBIT = Net Sales - Operating Expenses  
(Capital costs를 포함하지 않은 일반적인 측정방법)
{:.success}

EBIT는 손익계산서상의 **영업이익(일반적으로 매출이익에서 판매 및 일반관리비를 차감한 것)**에서 **비영업활동으로 인한 손익**을 차감하고 **영업외손익**과 **특별손익** 중 **영업활동**으로 인해 발생한 손익의 **이자 및 세전이익**을 산출한 금액이다.  

이렇게 산출된 EBIT는 채권자나 세무에 대한 채무가 없다고 가정하는 경우 기업이 얻을 수 있는 이익으로 정의될 수 있다. 즉, **부채조달에 따른 이자부담을 무시하는 경우의 기업 수익성 지표**로 활용될 수 있다.

EBIT의 가장 큰 장점은 기업의 경영성과를 평가하는 과정에서 차입금을 사용하는 기업이 차입금을 사용하지 않는 기업보다 수익성이 낮게 평가되는 것을 방지하며 **자본의 조달방식과는 무관하게 순수영업을 통한 기업의 수익성을 좀 더 정확하게 측정**할 수 있다는 것이다. 즉, 순수영업을 통한 수익성을 최대한 편향없이 동등한 조건하에서 비교해볼 수 있다.

결론적으로 EBIT를 사용함으로써 본영업활동으로 인한 자본수익률을 측정할 수 있고, 일반법이 각자 다른 이자부담과 세율의 불균형을 무시하고 비교했던 면을 보완하여 같은 조건하에서 객관적이고 공정한 비교를 가능케 하는 효과를 가져올 수 있다.

- **순운전자본(Net Working Caping)**  
일상적인 영업활동에 필요한 자금으로서 단기부채를 지급하는데 사용할 단기자산을 의미한다.

- **순고정자산**
기업의 사업운영과 관련하여 사용 또는 점유하고 있는 고정자산에서 무이자 고정부채를 차감한 순자산을 의미한다.

  
## 4. 이익수익률의 구성요소

**이익수익률(利益收益率, Earning Yield)**  
기업에 지불해야하는 가격 대비 해당기업이 벌어줄 수 있는 이윤의 비율  
$EY = \frac{EBIT}{기업가치(EV))} = \frac{EBIT}{시가총액(우선주 \ 포함) + 순이자 \ 부담부채}$
{:.success}