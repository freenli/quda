<template>
  <div id='page-top'>
    <nav id="mainNav" class="navbar navbar-default navbar-fixed-top" role="navigation">
      <div class="container-fluid">
        <div class="navbar-header">
          <a class="navbar-brand page-scroll" href="#page-top"  @click="smoothScroll($event)">QUDA</a>
        </div>

        <div id="bs-scrollspy">
          <ul class="nav navbar-nav navbar-right">
            <li>
              <a class="page-scroll" href="#details" @click="smoothScroll($event)">Six Dimensions</a>
            </li>
            <li>
              <a class="page-scroll" href="#overview"  @click="smoothScroll($event)">Overview</a>
            </li>
            <li>
              <a class="page-scroll" href="#freenli"  @click="smoothScroll($event)">Free-NLI</a>
            </li>
            <li>
              <a class="page-scroll" href="#team"  @click="smoothScroll($event)">Team</a>
            </li>
            <li>
              <a class="page-scroll" href="https://freenli.github.io/quda/"  @click="smoothScroll($event)">Download</a>
            </li>
            <li>
              <a class="page-scroll" href="#contact"  @click="smoothScroll($event)">Contact</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    
    <header>
      <div class="header-content">
        <div class="header-content-inner">
          <h1>{{ title }} </h1>
          <hr>
          <h3>{{ subtitle }}</h3>
          <p class="text-faded">
            {{ projectDesc }}
            <br><br>
            {{ projectSubDesc }}
          </p>
        </div>
      </div>
    </header>

    <section class="bg-primary" id="details">
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-lg-offset-2 text-center">
            <h2 class="section-heading">Six Dimensions</h2>
            <hr class="light">
            <div class="row six-dimensions" v-for="twoItems in aboutDetails" :key="twoItems[0][0]">
              <div class="col-md-6 col-sm-6 col-xs-12" v-for="item in twoItems" :key="item[0]">
                <div class="media" style="padding-bottom:10px">
                  <div class="media-left">
                    <img width="100" :src="item[2]" :alt="item[2]"  class="media-object img-rounded">
                  </div>
                  <div class="media-body" style="vertical-align:middle">
                    <p class="dimensions-text">{{ item[0] }}</p>
                    <p class="text-faded dimensions-text">{{ item[1] }}</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="overview">
      <div class="container">
        <div class="row" style="margin-top:20px">
          <div class="col-lg-8 col-lg-offset-2 text-center">
            <h2 class="section-heading">Corpus Overview</h2>
            <hr class="primary">
            <h3><i class="fa fa-tasks"></i> The analysis of 10 tasks</h3>
            <img width="100%" src="/img/overview.png" class="img-rounded">
          </div>
        </div>
        <div class="row" style="margin-top:20px">
          <div class="col-lg-8 col-lg-offset-2 text-center">
            <h3><i class="fa fa-table"></i> Samples</h3>
            <img width="100%" src="/img/infographic.png" class="img-rounded">
          </div>
        </div>
      </div>
    </section>


    <!-- <section class="no-padding" id="team">
      <div class="container-fluid">
        <div class="row no-gutter">
          <div class="col-md-2 col-sm-4 col-xs-6" v-for="member in members" :key="member.name">
            <a :href="member.url" class="portfolio-box" target="_blank">
              <img :src="'/img/members/' + member.photo" class="img-responsive" alt="">
              <div class="portfolio-box-caption">
                <div class="portfolio-box-caption-content">
                  <div class="project-name">
                    {{ member.name }}
                  </div>
                  <div class="project-category text-faded">
                    {{ member.affiliation }}
                  </div>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
    </section> -->

    <section id="contact" class="bg-dark">
      <div class="container">
        <div class="row">
          <div class="col-md-12 text-center">
            <h2 class="section-heading">{{ contactTitle }}</h2>
            <hr class="primary">
            <p>{{ contactDesc }}</p>
          </div>
          <div class="col-md-12 text-center">
            <i class="fa fa-envelope-o fa-3x wow bounceIn" data-wow-delay=".1s"></i>
            <p><a href="mailto:xdge@zju.edu">xdge@zju.edu</a></p>
          </div>
        </div>
      </div>
    </section>
    

  </div>
</template>

<script>
import $ from 'jquery'
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap/dist/js/bootstrap.min.js'
import 'bootstrap/dist/js/bootstrap.js'
import '../css/animate.min.css'
import 'font-awesome/css/font-awesome.min.css'

export default {
  name: 'HomePage',
  data() {
    return {
      title: 'QUDA',
      subtitle: 'Natural Language Queries for Visual Data Analytics',
      projectDesc: 'Visualization-oriented natural language interfaces (V-NLIs) have been explored and developed in recent years. One challenge faced by V-NLIs is in the formation of effective design decisions that usually requires a deep understanding of user queries. We present a new dataset, called Quda,  to help V-NLIs categorize queries into analytic tasks by training and benchmarking cutting-edge NLP techniques. Our corpus consists of a number of queries annotated with an analytic task and features high-quality, large-volume queries designed in the context of V-NLIs.',
      projectSubDesc: 'Quda contains 14,035 diverse user queries annotated with 10 low-level analytic tasks that assist in the deployment of state-of-the-art techniques for parsing complex human language.',
      aboutDetails: [
        [["Abstraction: Concrete", "Focus on the queries at the low abstraction level", "/img/icons/taxonomy.png"], ["Composition: Low", "10s of eye-tracking lab participants", "/img/icons/10s-of-people.png"]],
        [["Perspective: Objectives", "100s of labeled visualizations","/img/icons/100s-labeled-viz.png"], ["Type of Data: Table", "100s of memorability scores","/img/icons/100s-mem-scores.png"]],
        [["Type of Tasks: 10 Low-level Tasks", "100s of participants on Amazon’s Mechanical Turk","/img/icons/100s-of-people.png"], ["Context Dependency: Independent", '1000s of visualizations "in-the-wild"',"/img/icons/1000s-visualization.png"]],
      ],
      eyeTitle: 'Eye-movement Data',
      eyeDesc: 'We have eye-movement data for a total of 393 visualizations and 33 viewers, with an average of 16 viewers per visualization. Each viewer looked at each visualization for 10 seconds, generating an average of 37 fixation points. This is a total of about 600 fixation points per visualization across all viewers. We store the (x,y) location of each fixation on a visualization, the time-point when the fixation occurred during the viewing period, and the duration (in ms) of each fixation. We provide tools for visualizing the fixation sequences, fixation durations, and fixation heatmaps on top of visualizations.',
      bookChapters: [
        {
          title: "Eye Fixation Metrics for Large Scale Evaluation and Comparison of Information Visualizations",
          link: "http://link.springer.com/chapter/10.1007/978-3-319-47024-5_14",
          bibtex: "http://citation-needed.services.springer.com/v2/references/10.1007/978-3-319-47024-5_14?format=bibtex&flavour=citation",
          authors: "Bylinskii, Z., Borkin, M. A., Kim, N. W., Pfister, H., and Oliva, A.",
          source: "In Burch, M., Chuang, L., Fisher, B., Schmidt, A., Weiskopf, D. (Eds.), Eye Tracking and Visualization: Foundations, Techniques, and Applications (pp. 235-255). Springer International Publishing"
        }
      ],
      journalPapers: [
        {
          title: "BubbleView: an interface for crowdsourcing image importance maps and tracking visual attention",
          link: "https://vcg.seas.harvard.edu/publications/bubbleview-an-alternative-to-eye-tracking-for-crowdsourcing-image-importance/paper",
          site:"https://namwkim.github.io/bubbleview/",
          bibtex:"https://vcg.seas.harvard.edu/publications/bubbleview-an-alternative-to-eye-tracking-for-crowdsourcing-image-importance.bib",
          supplement:"https://vcg.seas.harvard.edu/publications/bubbleview-an-alternative-to-eye-tracking-for-crowdsourcing-image-importance/supplementary-material",
          authors: "Kim, N.W.<sup>*</sup>, Bylinskii, Z.<sup>*</sup>, Borkin, M., Gajos, K.Z., Oliva, A., Durand F., & Pfister, H.",
          source: "ACM Transactions on Computer-Human Interaction, 2017 (to appear)"
        },
        {
          title: "Beyond Memorability: Visualization Recognition and Recall",
          link: "http://vcg.seas.harvard.edu/files/pfister/files/infovis_submission251-camera.pdf",
          supplement: "http://vcg.seas.harvard.edu/files/pfister/files/infovis_submission251-supplementalmaterial-camera.pdf",
          video: "http://vcg.seas.harvard.edu/files/pfister/files/infovis-251_teaser.mp4",
          slides:"http://vcg.seas.harvard.edu/files/pfister/files/infovis-2015_final.pdf",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/534661",
          authors: "Borkin, M.<sup>*</sup>,  Bylinskii, Z.<sup>*</sup>, Kim, N.W., Bainbridge C.M., Yeh, C.S., Borkin, D., Pfister, H., & Oliva, A.",
          source: "IEEE Transactions on Visualization and Computer Graphics (Proceedings of InfoVis 2015)"
        },
        {
          title: "What Makes a Visualization Memorable?",
          link: "http://vcg.seas.harvard.edu/files/pfister/files/infovis_borkin-128-camera_ready_0.pdf",
          supplement: "http://vcg.seas.harvard.edu/files/pfister/files/supplemental-infovis128.pdf",
          video: "http://vcg.seas.harvard.edu/files/pfister/files/experiment-screengrab.mp4",
          slides:"http://vcg.seas.harvard.edu/files/pfister/files/infovis2013_borkin-vizmem.pdf",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/83476",
          authors: "Borkin, M., Vo, A., Bylinskii, Z., Isola, P., Sunkavalli, S., Oliva, A., & Pfister, H.",
          source: "IEEE Transactions on Visualization and Computer Graphics (Proceedings of InfoVis 2013)"
        }
      ],
      otherPapers:  [       
        {
          title: "Eye Fixation Metrics for Large Scale Analysis of Information Visualizations",
          link: "http://web.mit.edu/zoya/www/Bylinskii_eyefixations_small.pdf",
          slides:"http://web.mit.edu/zoya/www/ETVIS_red.pdf",
          //bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/371751",
          authors: "Bylinskii, Z., & Borkin, M.",
          source: "First Workshop on Eyetracking and Visualizations (ETVIS 2015) in conjunction with IEEE VIS 2015"
        },
        {
          title: "A Crowdsourced Alternative to Eye-tracking for Visualization Understanding",
          link: "https://vcg.seas.harvard.edu/publications/a-crowdsourced-alternative-to-eye-tracking-for-visualization-understanding/paper",
          slides:"https://vcg.seas.harvard.edu/publications/a-crowdsourced-alternative-to-eye-tracking-for-visualization-understanding/poster",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/371751",
          authors: "Kim, N.W., Bylinskii, Z., Borkin, M., Oliva, A., Gajos, K.Z., & Pfister, H.",
          site:"https://namwkim.github.io/bubbleview/",
          source: "Proceedings of the ACM Conference Extended Abstracts on Human Factors in Computing Systems (CHI EA '15)"
        }
      ],
      techReports: [],
      members: [        
        {
          name: "Michelle A. Borkin",
          url: "http://people.seas.harvard.edu/~borkin/",
          photo: "michelle.jpg",
          affiliation: "Assistant Professor, Northeastern CCIS"
        },
        {
          name: "Zoya Bylinskii",
          url: "http://web.mit.edu/zoya/www/",
          photo: "zoya.jpg",
          affiliation: "PhD Candidate, MIT EECS"
        },
        {
          name: "Krzysztof Z. Gajos",
          url: "http://www.eecs.harvard.edu/~kgajos/",
          photo: "gajos.jpg",
          affiliation: "Assosiate Professor, Harvard SEAS"
        },
        {
          name: "Nam Wook Kim",
          url: "http://namwkim.org",
          photo: "nam.png",
          affiliation: "PhD Candidate, Harvard SEAS"
        },
        {
          name: "Aude Oliva",
          url: "http://cvcl.mit.edu/audeoliva.html",
          photo: "aude.jpg",
          affiliation: "Principal Research Scientist, MIT CSAIL"
        },
        {
          name: "Hanspeter Pfister",
          url: "http://vcg.seas.harvard.edu/people/hanspeter-pfister",
          photo: "hp.jpg",
          affiliation: "Professor, Harvard SEAS"
        }
      ],
      datasetTitle: 'Dataset Download',
      license: 'By checking this box, you agree to the following license agreement: Access to, and use of, the images, and annotations in this dataset are for research and educational uses only. No commercial use, reproduction or distribution of the images, or any modifications thereof, is permitted. ',
      datasets: [
        {
          name: "all5k",
          size: "(~2.42G)",
          desc: "This data contains 5,814 single- and multi-panel visualizations scraped from the web from seven different online sources making up a total of four different source categories (government and world organizations, news media, infographics, and scientific publications). We provide the original visualizations, original URLs, source and category labels, as well as whether each visualization is single or multi-panel. This data is described in “What makes a visualization memorable?” (InfoVis 2013).",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/83476"
        },
        {
          name: "single2k",
          size: "(~625M)",
          desc: "This data contains a subset of the visualizations from all5k, limited to only single-panel, stand-alone visualizations (a total of 2,068 visualizations). We provide the original URLs, source and category labels, and visualization type. The taxonomy used to classify the visualization type is described in “What makes a visualization memorable?” (InfoVis 2013).",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/83476"
        },
        {
          name: "targets410",
          size: "(~140M)",
          desc: "This data contains taxonomic labels and attributes for 410 visualizations. These include the source, category, and type of each visualization, as well as the following attributes: data-ink ratio, number of distinctive colors, black & white, visual density, human recognizable object (HRO), and human depiction. We also provide the transcribed title for each visualization and where the title was located on the visualization. From the Amazon Mechanical Turk (AMT) Experiments, we provide the number of hits, misses, false alarms, and correct rejections per image, which can be converted into the desired memorability scores (HR, FAR, dprime, etc.)",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/83476"
        },
        {
          name: "targets393",
          size: "(~160M)",
          desc: "This data contains taxonomic labels and attributes for 393 visualizations. These include the source, category, and type of each visualization, as well as the following attributes: data-ink ratio, number of distinctive colors, black & white, visual density, human recognizable object (HRO), and human depiction. We also provide the transcribed title for each visualization and where the title was located on the visualization, as well as whether the visualization contained data or message redundancy. From Borkin et al. 2013 we include at-a-glance memorability scores (after 1 second of viewing) and from Borkin, Bylinskii et al. 2015 we include prolonged memorability scores (after 10 seconds of viewing). As described in “Beyond Memorability: Visualization Recognition and Recall“ (InfoVis 2015), we provide participant's eye movements and textual descriptions.",
          bibtex: "http://vcg.seas.harvard.edu/publications/export/bibtex/534661"
        }
      ],
      name: '',
      email: '',
      inst: '',
      instAddr: '',
      ivgrName: '',
      ivgrEmail: '',
      othrEmail: '',
      rqstResn: '',
      contactTitle: "Contact us!",
      contactDesc: "Questions? Comments?",
      acknowledgement: "This work has been supported in part by the National Science Foundation (NSF) under grant 1016862, MIT Big Data Initiative at CSAIL, Google, and Xerox awards to Aude Oliva. This work has also been made possible through support from the Department of Defense through the National Defense Science & Engineering Graduate Fellowship (NDSEG) Program, the NSF Graduate Research Fellowship Program, the Natural Sciences and Engineering Research Council of Canada Postgraduate Doctoral Scholarship (NSERC PGS-D), and the Kwanjeong Educational Foundation."

    }
  },
  methods: {
    smoothScroll: function (event) {
      var anchor = $(event.target)
      // $("html, body").animate({scrollTop: $(anchor.attr("href")).offset().top -20+ "px"}, 500)
      $('html, body').stop().animate({scrollTop: $(anchor.attr('href')).offset().top - 50}, 1250)
      event.preventDefault()
    },
    validateEmail: function (email) {
      var re = /^([\w-]+(?:\.[\w-]+)*)@((?:[\w-]+\.)*\w[\w-]{0,66})\.([a-z]{2,6}(?:\.[a-z]{2})?)$/i;
      return re.test(email);
    },
    downloadDataset: function () {
      if ($("#licensechk").prop('checked') == false) {
        $("#license-alert").show()
        setTimeout(function () {
          $("#license-alert").hide(400)
        }, 2000)
        return
      }
      //validate from data
      console.log(this.name + "," + this.email + "," + this.inst+ "," + this.instAddr+ "," + this.ivgrName + "," + this.ivgrEmail + "," + this.othrEmail+ "," + this.rqstResn)
      if (this.name == "" || this.email == "" || !this.validateEmail(this.email)) {
        console.log("not enough information")
        $("#request-alert").show()
        setTimeout(function () {
          $("#request-alert").hide(400)
        }, 2000)
        return
      }
      //request data
      var requested = []
      this.datasets.forEach(function (d) {
        if ($("#" + d.name).prop('checked')) {
          if (d.name == "all5k") {
            requested.push("news")
            requested.push("science")
            requested.push("government")
            requested.push("vis1")
            requested.push("vis2")
            requested.push("vis3")
          } else {
            requested.push(d.name)
          }
        }
      })
      if (requested.length == 0) {
        $("#data-alert").show()
        setTimeout(function () {
          $("#data-alert").hide(400)
        }, 2000)
        return
      }
      // var request = {
      //   name: this.name,
      //   email: this.email,
      //   inst: this.inst,
      //   inst_addr: this.instAddr,
      //   ivgr_name: this.ivgrName,
      //   ivgr_email: this.ivgrEmail,
      //   othr_email: this.othrEmail,
      //   rqst_resn: this.rqstResn,
      //   requested: requested
      // }
    }
  },
  mounted() {
    $("#mainNav").affix({
      offset: {
        top: 100
      }
    })
  }
}
</script>


<style>
@import "../css/creative.css";
</style>