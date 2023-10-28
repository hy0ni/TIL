# 마우스 이벤트(event) 종류

- [마우스 이벤트(event) 종류](#마우스-이벤트event-종류)
  - [click](#click)
  - [mousedown](#mousedown)
  - [mouseup](#mouseup)
  - [dblclick](#dblclick)
  - [mousemove](#mousemove)
  - [mouseover](#mouseover)
  - [mouseout](#mouseout)
  - [mouseenter](#mouseenter)
  - [mouseleave](#mouseleave)
  - [contextmenu](#contextmenu)
  - [mouseover, mouseout \& mouseenter, mouseleave 차이점](#mouseover-mouseout--mouseenter-mouseleave-차이점)

## click

사용자가 해당 element를 `클릭했을 때(버튼을 눌렀다가 떼었을 때)` 발생 한다.

## mousedown

사용자가 해당 element에서 `마우스 버튼을 눌렀을 때` 발생 한다.

## mouseup

사용자가 해당 element에서 `눌렀던 마우스 버튼을 떼었을 때` 발생 한다.

## dblclick

사용자가 해당 element에서 `마우스 버튼을 더블 클릭했을 때` 발생 한다.

## mousemove

사용자가 해당 element에서 `마우스를 움직였을 때` 발생 한다.

## mouseover

사용자가 마우스를 해당 element `바깥에서 안으로 옮겼을 때` 발생 한다.

## mouseout

사용자가 마우스를 해당 element `안에서 바깥으로 옮겼을 때` 발생 한다.

## mouseenter

사용자가 마우스를 해당 element `바깥에서 안으로 옮겼을 때` 발생 한다. 버블링이 발생하지 않음.

## mouseleave

사용자가 마우스를 해당 element `안에서 바깥으로 옮겼을 때` 발생 한다. 버블링이 발생하지 않음.

## contextmenu

마우스 오른쪽 버튼을 눌렀을 때 발생한다.

contextmenu 이벤트를 발생시키면, context 메뉴가 나타남.
contextmenu 이벤트는 element에서 마우스 오른쪽 버튼을 클릭했을 때 발생하며, click 이벤트와 같이 mousedown, mouseup 이벤트도 같이 발생한다.

## mouseover, mouseout & mouseenter, mouseleave 차이점

`mouseOver, mouseOut`
이벤트가 발생할 때 버블링이 일어나며 상위 요소로 전파된다.
preventDefault 메서드를 호출하여 이벤트의 기본 동작을 취소할 수 있다.

`mouseEnter, mouseLeave`
이벤트가 발생할 때 버블링이 일어나지 않아 자기 자신만이 이벤트를 받을 수 있게 된다. 즉 target과 currentTarget이 항상 일치한다.
preventDefault 메서드를 호출하여 이벤트의 기본 동작을 취소할 수 없다. (bubbles: false; cancelable: false;)
