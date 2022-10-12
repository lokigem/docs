<style>
    section#timeline {
    width: 80%;
    margin: 20% auto;
    position: relative;
}

section#timeline::before {
    content: '';
    display: block;
    position: absolute;
    left:50%;
    top: 0;
    margin: 0 0 0 -1px;
    width: 2px;
    height: 100%;
    background: rgba(255,255,255,0,2);
}

section#timeline article {
    width: 100%;
    margin: 0 0 20px 0;
    position: relative;
}

section#timeline article:after{
    content:'';
    display: block;
    clear: both;
}

section#timeline article div.inner {
    width: 40%;
    float: left;
    margin: 5px 0 0 0;
    border-radius: 6px;
}

section#timeline article div.inner span.date{
    display: block;
    padding: 20px 5px;
    position: absolute;
    width: 60px;
    height: 60px;
    top: 0;
    left: 50%;
    margin: 0 0 0 -20px;
    border-radius: 100%;
    font-size: 12px;
    font-weight: 900;
    background: #DCDCDC;
    color: black;
    border: 2px solid rgba(255,255,255,0,2);
    box-shadow: 0 0 0 7px #DCDCDC;
}

section#timeline article div.inner span.year span {
    display: block;
    text-align: center;
}

section#timeline article div.inner span.date span.year {
    text-align: center;
    font-size: 18px;
    color: black;
}

section#timeline article div.inner h2 {
    padding: 15px;
    margin: 0;
    color: black;
    font-weight: bold;
    font-family: sans;
    font-size: 20px;
    text-transform: uppercase;
    letter-spacing: -1px;
    border-radius: 6px 6px 0 0;
    position: relative;
}

section#timeline article div.inner h2:after {
    content: '';
    position: absolute;
    top:20px;
    right: -5px;
    width:10px;
    height: 10px;
    -webkit-transform: rotate(45deg);
}

section#timeline article div.inner p {
    padding: 15px;
    margin: 0;
    font-size: 14px;
    background: #FFF;
    color: #656565;
    border-radius: 0 0 6px 6px;
}

section#timeline article:nth-child(2n+2) div.inner {
    float: right;
  }
  section#timeline article:nth-child(2n+2) div.inner h2:after {
    left: -5px;
  }
  section#timeline article:nth-child(2) div.inner h2 {
    background: #E74C3C;
  }
  section#timeline article:nth-child(2) div.inner h2:after {
    background: #E74C3C;
  }
  section#timeline article:nth-child(3) div.inner h2 {
    background: #2ECC71;
  }
  section#timeline article:nth-child(3) div.inner h2:after {
    background: #2ECC71;
  }
  section#timeline article:nth-child(4) div.inner h2 {
    background: #E67E22;
  }
  section#timeline article:nth-child(4) div.inner h2:after {
    background: #E67E22;
  }
  section#timeline article:nth-child(5) div.inner h2 {
    background: #1ABC9C;
  }
  section#timeline article:nth-child(5) div.inner h2:after {
    background: #1ABC9C;
  }
  section#timeline article:nth-child(6) div.inner h2 {
    background: #9B59B6;
  }
  section#timeline article:nth-child(6) div.inner h2:after {
    background: #9B59B6;
  }
    section#timeline article:nth-child(7) div.inner h2 {
        background: #FFF00F;
      }
      section#timeline article:nth-child(7) div.inner h2:after {
        background: #FFF00F;

      }
</style>
<section id="timeline">
  <div class="textbox">
 <p>Timeline</p>
</div>

 <article>
     <div class="inner">
         <span class="year">
             <span class="date">9.17</span>
         </span>
         <h2>Flutter 개발 시작</h2>
         <p>Flutter를 활용해서 Multi Platform Application 출시 도전</p>
     </div>
 </article>
<article>
     <div class="inner">
         <span class="date">
             <span class="year">2022</span>
         </span>
     </div>
 </article>



 </section>