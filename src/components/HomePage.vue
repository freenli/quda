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
              <a class="page-scroll" href="#details" @click="smoothScroll($event)">Dimensions</a>
            </li>
            <li>
              <a class="page-scroll" href="#preview"  @click="smoothScroll($event)">Preview</a>
            </li>
            <!-- <li>
              <a class="page-scroll" href="#freenli"  @click="smoothScroll($event)">Free-NLI</a>
            </li> -->
            <!-- <li>
              <a class="page-scroll" href="#team"  @click="smoothScroll($event)">Team</a>
            </li> -->
            <li>
              <a class="page-scroll" href="https://drive.google.com/file/d/1AUTbV4mV1YHXZ0g1tPU3lb6JJypqtc3s/view?usp=sharing"  @click="smoothScroll($event)">Download</a>
            </li>
            <!-- <li>
              <a class="page-scroll" href="#contact"  @click="smoothScroll($event)">Contact</a>
            </li> -->
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
            <!-- <br><br>
            {{ projectSubDesc }} -->
          </p>
        </div>
      </div>
    </header>

    <section class="bg-primary" id="details">
      <div class="container">
        <div class="row">
          <div class="col-lg-10 col-lg-offset-2 text-center">
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

    <section id="preview">
      <div class="container corpus-preview">
        <div class="row" style="margin-top:20px">
          <div class="text-center">
            <h2 class="section-heading"> <i class="fa fa-table"></i> Corpus Preview</h2>
            <hr class="primary">
            <vue-good-table :columns="columns" :rows="rows" :line-numbers="true">
              <div slot="table-actions">
                <button class="btn" @click="download()">Download</button> 
              </div>
            </vue-good-table>
            <div class="tips">
              <h4>Tips:</h4>
              <p style="margin-bottom: 0;">task_id: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;task id of the sentence(1-10) </p>
              <p style="margin-bottom: 0;">exp_sen_id: expert sentence id of the sentence(1-920)</p>
              <p style="margin-bottom: 0;">is_exp_sen: whether the sentence is the expert sentence(0: no, 1: yes)</p>
              <p style="margin-bottom: 0;">table_id: table id of the sentence(1-37)</p>
              <p style="margin-bottom: 0;">expert_id: expert id of the sentence(1-20)</p>
            </div>
            <!-- <h3><i class="fa fa-table"></i> The analysis of 10 tasks</h3> -->
          </div>
        </div>
        <!-- <div class="row" style="margin-top:20px">
          <div class="col-lg-8 col-lg-offset-2 text-center">
            <h3><i class="fa fa-table"></i> Samples</h3>
            <img width="100%" src="/img/infographic.png" class="img-rounded">
          </div>
        </div> -->
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

    <!-- <section id="contact" class="bg-dark">
      <div class="container">
        <div class="row">
          <div class="col-md-12 text-center">
            <h2 class="section-heading">{{ contactTitle }}</h2>
            <hr class="primary">
          </div>
          <div class="col-md-12 text-center">
            <i class="fa fa-envelope-o fa-3x wow bounceIn" data-wow-delay=".1s"></i>
            <p><a href="mailto:xdge1996@gmail.com">xdge1996@gmail.com</a></p>
          </div>
        </div>
      </div>
    </section> -->
    

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
import 'vue-good-table/dist/vue-good-table.css'
import { VueGoodTable } from 'vue-good-table'

export default {
  name: 'HomePage',
  components: {
  VueGoodTable,
},
  data() {
    return {
      title: 'QUDA',
      subtitle: 'Natural Language Queries for Visual Data Analytics',
      projectDesc: 'In the context of visualization-oriented natural language interfaces, Quda contains 14,035 diverse user queries annotated with 10 low-level analytic tasks that assist in the deployment of state-of-the-art machine/deep learning techniques for parsing complex human language.',
      projectSubDesc: 'Quda contains 14,035 diverse user queries annotated with 10 low-level analytic tasks that assist in the deployment of state-of-the-art techniques for parsing complex human language.',
      aboutDetails: [
        [["Abstraction: Low", "The abstraction level describes how concrete a query is.", "/img/icons/abstraction.png"], ["Composition: Low", "The composition level describes to what extent a query encompasses sub-queries.", "/img/icons/composition.png"]],
        [["Perspective: Objectives", "Instead of enumerating actions, we aim to collect queries that are objectives raised by data analysts.","/img/icons/perspective.png"], ["Type of Data: Table", "Data and dataset can be categorized into five types, i.e., table, networks & trees, fields, geometry, and clusters & sets & lists.","/img/icons/table.png"]],
        [["Type of Tasks: 10 Low-level Tasks", " Retrieve Value, Correlate, Compute Derived Value, Find Anomalies, etc.","/img/icons/tasks.png"], ["Context Dependency: Independent", "Focus on queries that have complete references to tasks or values associated with a task.","/img/icons/context.png"]],
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
      acknowledgement: "This work has been supported in part by the National Science Foundation (NSF) under grant 1016862, MIT Big Data Initiative at CSAIL, Google, and Xerox awards to Aude Oliva. This work has also been made possible through support from the Department of Defense through the National Defense Science & Engineering Graduate Fellowship (NDSEG) Program, the NSF Graduate Research Fellowship Program, the Natural Sciences and Engineering Research Council of Canada Postgraduate Doctoral Scholarship (NSERC PGS-D), and the Kwanjeong Educational Foundation.",
      columns: [
        {
          label: 'task_id',
          field: 'task_id',
          type: 'number',
          tdClass: 'table-text-center',
          width: '70px',
        },
        {
          label: 'exp_sen_id',
          field: 'exp_sen_id',
          type: 'number',
          tdClass: 'table-text-center',
          width: '100px',
        },
        {
          label: 'is_exp_sen',
          field: 'is_exp_sen',
          type: 'number',
          tdClass: 'table-text-center',
          width: '95px',
        },
        {
          label: 'table_id',
          field: 'table_id',
          type: 'number',
          tdClass: 'table-text-center',
          width: '80px',
        },
        {
          label: 'expert_id',
          field: 'expert_id',
          type: 'number',
          tdClass: 'table-text-center',
          width: '85px',
        },
        {
          label: 'sentence',
          field: 'sentence',
          type: 'text',
          width: '400px',
        }
      ],
      rows: [
        { id:1, task_id:"1", exp_sen_id: 1, is_exp_sen: 0, table_id: 1, expert_id: 1, sentence: 'show me arkansas\' population on july 1 , 2002 .'},
        { id:2, task_id:"1", exp_sen_id: 715, is_exp_sen: 1, table_id: 35, expert_id: 16, sentence: 'how many residents in orange county are asians ?'},
        { id:3, task_id:"2", exp_sen_id: 90, is_exp_sen: 0, table_id: 11, expert_id: 3, sentence: 'can you tell me the team that won the game ?'},
        { id:4, task_id:"2", exp_sen_id: 91, is_exp_sen: 1, table_id: 7, expert_id: 3, sentence: 'which country has more females than males ?'},
        { id:5, task_id:"3", exp_sen_id: 105, is_exp_sen: 0, table_id: 3, expert_id: 4, sentence: 'in western europe , what is the average gdp ?'},
        { id:6, task_id:"3", exp_sen_id: 171, is_exp_sen: 1, table_id: 13, expert_id: 5, sentence: 'on average , how long are the books published by dark horse comics ?'},
        { id:7, task_id:"4", exp_sen_id: 246, is_exp_sen: 0, table_id: 15, expert_id: 6, sentence: 'i would like to have the highest rating number .'},
        { id:8, task_id:"4", exp_sen_id: 262, is_exp_sen: 1, table_id: 1, expert_id: 1, sentence: 'what is the longest study time that students have ?'},
        { id:9, task_id:"5", exp_sen_id: 358, is_exp_sen: 1, table_id: 21, expert_id: 7, sentence: 'list all the expensive apps , from the most recent to the oldest .'},
        { id:10, task_id:"5", exp_sen_id: 378, is_exp_sen: 0, table_id: 22, expert_id: 8, sentence: 'list all the movies according to their release year .'},
        { id:11, task_id:"6", exp_sen_id: 433, is_exp_sen: 1, table_id: 24, expert_id: 9, sentence: 'what is the range of the number of undergraduate students ?'},
        { id:12, task_id:"6", exp_sen_id: 491, is_exp_sen: 0, table_id: 26, expert_id: 10, sentence: 'in the south american countries , how large is the range of registered soccer players ?'},
        { id:13, task_id:"7", exp_sen_id: 770, is_exp_sen: 0, table_id: 36, expert_id: 17, sentence: 'determine the value distribution of deaf -blind patients .'},
        { id:14, task_id:"7", exp_sen_id: 810, is_exp_sen: 1, table_id: 32, expert_id: 18, sentence: 'show me the distribution of the population ratio binned with a bin size of 0.5 .'},
        { id:15, task_id:"8", exp_sen_id: 236, is_exp_sen: 1, table_id: 15, expert_id: 6, sentence: 'is there any app that is significantly different from the others ?'},
        { id:16, task_id:"8", exp_sen_id: 441, is_exp_sen: 0, table_id: 24, expert_id: 9, sentence: 'identify the anomalous values of both postgraduate and undergraduate income .'},
        { id:17, task_id:"9", exp_sen_id: 916, is_exp_sen: 0, table_id: 32, expert_id: 20, sentence: 'group the length of trip by initial sites .'},
        { id:18, task_id:"9", exp_sen_id: 532, is_exp_sen: 1, table_id: 27, expert_id: 11, sentence: 'find the cluster with the highest number of births among the neighborhoods across the years .'},
        { id:19, task_id:"10", exp_sen_id: 80, is_exp_sen: 1, table_id: 3, expert_id: 2, sentence: 'can we infer that higher freedom leads to higher happiness ?'},
        { id:20, task_id:"10", exp_sen_id: 613, is_exp_sen: 0, table_id: 30, expert_id: 13, sentence: 'are the ages of the actors and their winning results correlated ?'},
      ],
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
    },
    download: function () {
      window.location.href="https://drive.google.com/file/d/1AUTbV4mV1YHXZ0g1tPU3lb6JJypqtc3s/view?usp=sharing";
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