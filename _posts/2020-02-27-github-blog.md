---
layout: post
title: 블로그 생성 가이드(hasoo.github.io)
tags: blog
categories: Etc
---

# Jekyll(지킬)
* 정적 사이트 생성기
	* ruby
	* markdown
* 테마
	*<http://jekyllthemes.org/>

## hasoo.github.io 만들기
* ruby 설치
	* sudo apt install ruby-dev
	* gem update --system
* github 에 저장소 생성
	* Hasoo.github.io 이름으로 Repository 생성
	* git clone 저장소주소
* 지킬 테마 다운로드
	* <http://jekyllthemes.org/themes/tiffany/> 에서 Download
	* 테마를 내 로컬 저장소에 복사
	* \_config.yml 수정
	* swiftype, gitment 필요시 수정, 현재 수정 하지 않음
* github 에 등록
	* git commit -a -m ...
	* git push
* 포스팅
	* <https://devinlife.com/howto/> 참고