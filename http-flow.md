# http-flow
digraph G {

  start [
    label = "start";
    shape = oval;
  ];
  browser [
     label = "browser";
     shape = rect;
  ];
  url [
     label = "enter url http";
     shape = rect;
];
  status [
     label = "Resolved IP:add\n IP:Name";
     shape = diamond;
  ];

process [
    label = "is ther problem \nwith the Request ";
    shape = diamond;
];
r1 [
        label = "5xx Respond\n server does not support";
        shape = rect;
    ];

r2 [
        label = "4xx Respond\nError:server cannot or will\nnot process";
        shape = rect;
        ];

r3 [
    label = "1xx \nRespondserver has received \nthe request and is \ncontinuing the process";
        shape = rect;
        ];
r4 [
    label = "2xx_3xx \nRespond successful – \nthe request was successfully \nreceived, understood";
        shape = rect;
        ];
  end [
     label = "End";
     shape = oval;
  ];


start -> browser;
browser -> url;
url -> status;
status ->process;
process ->r1 [ label = "False" ];
process -> r2 [ label = "False" ];
process ->r3 
r3 ->end
r3 ->r4 [ label = "True" ];
process ->r4 [ label = "True" ];
r4 ->end
r2 -> start
r1  -> start
}

}
