{
  "version": "1.2",
  "package": {
    "name": "",
    "version": "",
    "description": "",
    "author": "",
    "image": ""
  },
  "design": {
    "board": "TinyFPGA-BX",
    "graph": {
      "blocks": [
        {
          "id": "61857e4b-ceec-4530-a1d4-5b4d50c60e86",
          "type": "basic.output",
          "data": {
            "name": "rs",
            "pins": [
              {
                "index": "0",
                "name": "PIN_1",
                "value": "A2"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1720,
            "y": 168
          }
        },
        {
          "id": "495621e0-d46f-47f5-8a2e-aefbcb0499c2",
          "type": "basic.output",
          "data": {
            "name": "rw",
            "pins": [
              {
                "index": "0",
                "name": "PIN_3",
                "value": "B1"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1744,
            "y": 304
          }
        },
        {
          "id": "1238757b-4774-482b-9bae-b2d5944f0a38",
          "type": "basic.output",
          "data": {
            "name": "d7",
            "pins": [
              {
                "index": "0",
                "name": "PIN_7",
                "value": "D1"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1752,
            "y": 408
          }
        },
        {
          "id": "bda8d021-7342-419e-8daf-91f96919669a",
          "type": "basic.output",
          "data": {
            "name": "d6",
            "pins": [
              {
                "index": "0",
                "name": "PIN_6",
                "value": "D2"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1688,
            "y": 488
          }
        },
        {
          "id": "840c52a8-9f9b-426e-906f-e98bf30ff882",
          "type": "basic.output",
          "data": {
            "name": "d5",
            "pins": [
              {
                "index": "0",
                "name": "PIN_5",
                "value": "C1"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1856,
            "y": 528
          }
        },
        {
          "id": "2f497d7f-0e8c-4b9d-93a0-489f5fadabb1",
          "type": "basic.output",
          "data": {
            "name": "d4",
            "pins": [
              {
                "index": "0",
                "name": "PIN_4",
                "value": "C2"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1832,
            "y": 616
          }
        },
        {
          "id": "cc50db8b-5ca9-4f7c-a884-8426af21e2c2",
          "type": "basic.output",
          "data": {
            "name": "en",
            "pins": [
              {
                "index": "0",
                "name": "PIN_2",
                "value": "A1"
              }
            ],
            "virtual": false
          },
          "position": {
            "x": 1696,
            "y": 696
          }
        },
        {
          "id": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
          "type": "basic.code",
          "data": {
            "code": "parameter n=27;\nparameter k=18;\n\nreg [n-1:0] count=0;\nreg lcd_busy=1;\nreg lcd_stb;\nreg [5:0] lcd_code;\nreg [6:0] lcd_stuff;\n\nreg lcd_rs;\nreg lcd_rw;\nreg lcd_7;\nreg lcd_6;\nreg lcd_5;\nreg lcd_4;\nreg lcd_e;\n\nalways @ (posedge clk) begin\n  count <= count + 1;\n  case(count[k+7:k+2])\n    0: lcd_code <= 6'b000010; // function set\n    1: lcd_code <= 6'b000010;\n    2: lcd_code <= 6'b001100;\n    3: lcd_code <= 6'b000000; // display on/off\n    4: lcd_code <= 6'b001100;\n    5: lcd_code <= 6'b000000; // display clear\n    6: lcd_code <= 6'b000001;\n    7: lcd_code <= 6'b000000; // entry mode set\n    8: lcd_code <= 6'b000110;\n    9: lcd_code <= 6'h24; // H\n    10: lcd_code <= 6'h28;\n    11: lcd_code <= 6'h26; // e\n    12: lcd_code <= 6'h25;\n    13: lcd_code <= 6'h26; // l\n    14: lcd_code <= 6'h2C;\n    15: lcd_code <= 6'h26; // l\n    16: lcd_code <= 6'h2C;\n    17: lcd_code <= 6'h26; // o\n    18: lcd_code <= 6'h2F;\n    19: lcd_code <= 6'h22; // SPC\n    20: lcd_code <= 6'h20;\n    21: lcd_code <= 6'h25; // W\n    22: lcd_code <= 6'h27;\n    23: lcd_code <= 6'h26; // o\n    24: lcd_code <= 6'h2F;\n    25: lcd_code <= 6'h27; // r\n    26: lcd_code <= 6'h22;\n    27: lcd_code <= 6'h26; // l\n    28: lcd_code <= 6'h2C; \n    29: lcd_code <= 6'h26; // d\n    30: lcd_code <= 6'h24;\n    31: lcd_code <= 6'h22; // !\n    32: lcd_code <= 6'h21;\n    default: lcd_code <= 6'b010000;\n  endcase\n  if(lcd_rw)\n    lcd_busy <= 0;\n  lcd_stb <= ^count[k+1:k+0] & ~lcd_rw & lcd_busy; // clkrate / 2^(k+2)\n  lcd_stuff <= {lcd_stb,lcd_code};\n  {lcd_e, lcd_rs, lcd_rw, lcd_7, lcd_6, lcd_5, lcd_4} <= lcd_stuff;\nend\n",
            "params": [],
            "ports": {
              "in": [
                {
                  "name": "clk"
                }
              ],
              "out": [
                {
                  "name": "lcd_rs"
                },
                {
                  "name": "lcd_rw"
                },
                {
                  "name": "lcd_7"
                },
                {
                  "name": "lcd_6"
                },
                {
                  "name": "lcd_5"
                },
                {
                  "name": "lcd_4"
                },
                {
                  "name": "lcd_e"
                }
              ]
            }
          },
          "position": {
            "x": 560,
            "y": 224
          },
          "size": {
            "width": 1048,
            "height": 536
          }
        }
      ],
      "wires": [
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_rs"
          },
          "target": {
            "block": "61857e4b-ceec-4530-a1d4-5b4d50c60e86",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_7"
          },
          "target": {
            "block": "1238757b-4774-482b-9bae-b2d5944f0a38",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_6"
          },
          "target": {
            "block": "bda8d021-7342-419e-8daf-91f96919669a",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_5"
          },
          "target": {
            "block": "840c52a8-9f9b-426e-906f-e98bf30ff882",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_4"
          },
          "target": {
            "block": "2f497d7f-0e8c-4b9d-93a0-489f5fadabb1",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_e"
          },
          "target": {
            "block": "cc50db8b-5ca9-4f7c-a884-8426af21e2c2",
            "port": "in"
          }
        },
        {
          "source": {
            "block": "3d604ae9-dbe6-442d-bbdd-34f6d5c025d4",
            "port": "lcd_rw"
          },
          "target": {
            "block": "495621e0-d46f-47f5-8a2e-aefbcb0499c2",
            "port": "in"
          }
        }
      ]
    }
  },
  "dependencies": {}
}
