{
    "metadata": {
        "kernelspec": {
            "name": "SQL",
            "display_name": "SQL",
            "language": "sql"
        },
        "language_info": {
            "name": "sql",
            "version": ""
        }
    },
    "nbformat_minor": 2,
    "nbformat": 4,
    "cells": [
        {
            "cell_type": "markdown",
            "source": [
                "# **Exploring data from my Fantasy Football Manager Rating project**"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "0b6e9fe2-3a12-4b85-9c7a-7df69389e496"
            },
            "attachments": {}
        },
        {
            "cell_type": "markdown",
            "source": [
                "**Let's start by examing the lowest rating:**"
            ],
            "metadata": {
                "azdata_cell_guid": "6b4dfe29-05fe-4b39-b6af-b923ada4f9c4",
                "language": ""
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, week_of_season, season \r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr \r\n",
                "LIMIT 1"
            ],
            "metadata": {
                "azdata_cell_guid": "16c27f56-91db-425c-9343-b9891d151563",
                "language": "sql",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(1 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.006"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 3,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Sean",
                                    "1": "836.9054042",
                                    "2": "6",
                                    "3": "2022"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>week_of_season</th><th>season</th></tr><tr><td>Sean</td><td>836.9054042</td><td>6</td><td>2022</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 3
        },
        {
            "cell_type": "markdown",
            "source": [
                "Taking a closer look at the beginning of the 2022 season, Sean entered the year with a 868.95 rating and even defeated a near 1100 rated opponent in week 1. Unfortunately for him, he scored below the median in week 1, so his rating didn't increase \n",
                "\n",
                "by that much. Following that, he lost his next 4 matchups, plummeting his rating to the lowest in league history."
            ],
            "metadata": {
                "azdata_cell_guid": "3fab6b75-f17e-4aeb-a681-2211155c7992"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, score, opponent, opponent_ffmr, winner, week_of_season, season\r\n",
                "FROM elo.timeline\r\n",
                "WHERE team = \"Sean\" and season = '2022'\r\n",
                "LIMIT 7"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "9c787181-54aa-47ee-9e32-e2384de8f9bd",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(7 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.030"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 41,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "score"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "winner"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Sean",
                                    "1": "868.9462139",
                                    "2": "113.78",
                                    "3": "John",
                                    "4": "1099.323164",
                                    "5": "Sean",
                                    "6": "1",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "875.0141916",
                                    "2": "64.44",
                                    "3": "Loof",
                                    "4": "1129.54885",
                                    "5": "Loof",
                                    "6": "2",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "866.2581202",
                                    "2": "109.5",
                                    "3": "Nick",
                                    "4": "1095.120116",
                                    "5": "Nick",
                                    "6": "3",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "857.1021804",
                                    "2": "86.62",
                                    "3": "Nate",
                                    "4": "1051.860391",
                                    "5": "Nate",
                                    "6": "4",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "848.2435304",
                                    "2": "107.04",
                                    "3": "Shev",
                                    "4": "923.9621109",
                                    "5": "Shev",
                                    "6": "5",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "836.9054042",
                                    "2": "120.8",
                                    "3": "Justin",
                                    "4": "936.805472",
                                    "5": "Sean",
                                    "6": "6",
                                    "7": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "858.2465871",
                                    "2": "119.56",
                                    "3": "Pfeff",
                                    "4": "929.1462149",
                                    "5": "Sean",
                                    "6": "7",
                                    "7": "2022"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>score</th><th>opponent</th><th>opponent_ffmr</th><th>winner</th><th>week_of_season</th><th>season</th></tr><tr><td>Sean</td><td>868.9462139</td><td>113.78</td><td>John</td><td>1099.323164</td><td>Sean</td><td>1</td><td>2022</td></tr><tr><td>Sean</td><td>875.0141916</td><td>64.44</td><td>Loof</td><td>1129.54885</td><td>Loof</td><td>2</td><td>2022</td></tr><tr><td>Sean</td><td>866.2581202</td><td>109.5</td><td>Nick</td><td>1095.120116</td><td>Nick</td><td>3</td><td>2022</td></tr><tr><td>Sean</td><td>857.1021804</td><td>86.62</td><td>Nate</td><td>1051.860391</td><td>Nate</td><td>4</td><td>2022</td></tr><tr><td>Sean</td><td>848.2435304</td><td>107.04</td><td>Shev</td><td>923.9621109</td><td>Shev</td><td>5</td><td>2022</td></tr><tr><td>Sean</td><td>836.9054042</td><td>120.8</td><td>Justin</td><td>936.805472</td><td>Sean</td><td>6</td><td>2022</td></tr><tr><td>Sean</td><td>858.2465871</td><td>119.56</td><td>Pfeff</td><td>929.1462149</td><td>Sean</td><td>7</td><td>2022</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 41
        },
        {
            "cell_type": "markdown",
            "source": [
                "Here's a bar graph of Sean's rating, so you can see the highs and lows. It appears that he'll be entering into next season with a rating of around 900, let's hope he can make a return to his previous form and start competing for the championship again.\n",
                "\n",
                "(You can find more detailed visualizations on my Tableau Public profile: https://public.tableau.com/app/profile/john.bolger )"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "28593bad-9a93-4d11-8215-a978dbd52e10"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT ffmr\r\n",
                "FROM elo.timeline\r\n",
                "WHERE team = \"Sean\""
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "b7a3eac7-1cfe-4d7c-88b0-b39c856d9623",
                "tags": [
                    "hide_input"
                ]
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(76 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.006"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 39,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "ffmr"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "1016.0"
                                },
                                {
                                    "0": "1017.001196"
                                },
                                {
                                    "0": "1032.860132"
                                },
                                {
                                    "0": "1048.271492"
                                },
                                {
                                    "0": "1030.563174"
                                },
                                {
                                    "0": "1044.177398"
                                },
                                {
                                    "0": "1056.997747"
                                },
                                {
                                    "0": "1070.830017"
                                },
                                {
                                    "0": "1083.130526"
                                },
                                {
                                    "0": "1095.747795"
                                },
                                {
                                    "0": "1109.574896"
                                },
                                {
                                    "0": "1121.409774"
                                },
                                {
                                    "0": "1087.892711"
                                },
                                {
                                    "0": "1068.929856"
                                },
                                {
                                    "0": "1072.43691"
                                },
                                {
                                    "0": "1051.95435"
                                },
                                {
                                    "0": "1033.017055"
                                },
                                {
                                    "0": "1048.652979"
                                },
                                {
                                    "0": "1044.154361"
                                },
                                {
                                    "0": "1026.072846"
                                },
                                {
                                    "0": "1022.636727"
                                },
                                {
                                    "0": "1038.735512"
                                },
                                {
                                    "0": "1020.753779"
                                },
                                {
                                    "0": "1035.045174"
                                },
                                {
                                    "0": "1016.470377"
                                },
                                {
                                    "0": "1031.806778"
                                },
                                {
                                    "0": "1045.781546"
                                },
                                {
                                    "0": "1027.6267"
                                },
                                {
                                    "0": "1010.52747"
                                },
                                {
                                    "0": "987.6894973"
                                },
                                {
                                    "0": "972.6050383"
                                },
                                {
                                    "0": "956.4017015"
                                },
                                {
                                    "0": "958.0696085"
                                },
                                {
                                    "0": "977.2477997"
                                },
                                {
                                    "0": "962.8812738"
                                },
                                {
                                    "0": "948.437185"
                                },
                                {
                                    "0": "933.7057925"
                                },
                                {
                                    "0": "920.4967705"
                                },
                                {
                                    "0": "909.5693409"
                                },
                                {
                                    "0": "897.0465147"
                                },
                                {
                                    "0": "884.4440656"
                                },
                                {
                                    "0": "888.6801555"
                                },
                                {
                                    "0": "879.2400453"
                                },
                                {
                                    "0": "867.1186603"
                                },
                                {
                                    "0": "870.0634374"
                                },
                                {
                                    "0": "892.364888"
                                },
                                {
                                    "0": "880.9312381"
                                },
                                {
                                    "0": "871.3117786"
                                },
                                {
                                    "0": "893.0221418"
                                },
                                {
                                    "0": "916.1102815"
                                },
                                {
                                    "0": "904.5961527"
                                },
                                {
                                    "0": "892.6420615"
                                },
                                {
                                    "0": "897.5143327"
                                },
                                {
                                    "0": "898.0384918"
                                },
                                {
                                    "0": "887.7455088"
                                },
                                {
                                    "0": "908.3223305"
                                },
                                {
                                    "0": "897.4882383"
                                },
                                {
                                    "0": "887.0388245"
                                },
                                {
                                    "0": "877.3773574"
                                },
                                {
                                    "0": "865.8804839"
                                },
                                {
                                    "0": "868.9462139"
                                },
                                {
                                    "0": "875.0141916"
                                },
                                {
                                    "0": "866.2581202"
                                },
                                {
                                    "0": "857.1021804"
                                },
                                {
                                    "0": "848.2435304"
                                },
                                {
                                    "0": "836.9054042"
                                },
                                {
                                    "0": "858.2465871"
                                },
                                {
                                    "0": "879.0791764"
                                },
                                {
                                    "0": "886.0698818"
                                },
                                {
                                    "0": "875.3899783"
                                },
                                {
                                    "0": "898.6773628"
                                },
                                {
                                    "0": "889.2201579"
                                },
                                {
                                    "0": "895.2892317"
                                },
                                {
                                    "0": "885.2927007"
                                },
                                {
                                    "0": "872.2541967"
                                },
                                {
                                    "0": "892.5651384"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>ffmr</th></tr><tr><td>1016.0</td></tr><tr><td>1017.001196</td></tr><tr><td>1032.860132</td></tr><tr><td>1048.271492</td></tr><tr><td>1030.563174</td></tr><tr><td>1044.177398</td></tr><tr><td>1056.997747</td></tr><tr><td>1070.830017</td></tr><tr><td>1083.130526</td></tr><tr><td>1095.747795</td></tr><tr><td>1109.574896</td></tr><tr><td>1121.409774</td></tr><tr><td>1087.892711</td></tr><tr><td>1068.929856</td></tr><tr><td>1072.43691</td></tr><tr><td>1051.95435</td></tr><tr><td>1033.017055</td></tr><tr><td>1048.652979</td></tr><tr><td>1044.154361</td></tr><tr><td>1026.072846</td></tr><tr><td>1022.636727</td></tr><tr><td>1038.735512</td></tr><tr><td>1020.753779</td></tr><tr><td>1035.045174</td></tr><tr><td>1016.470377</td></tr><tr><td>1031.806778</td></tr><tr><td>1045.781546</td></tr><tr><td>1027.6267</td></tr><tr><td>1010.52747</td></tr><tr><td>987.6894973</td></tr><tr><td>972.6050383</td></tr><tr><td>956.4017015</td></tr><tr><td>958.0696085</td></tr><tr><td>977.2477997</td></tr><tr><td>962.8812738</td></tr><tr><td>948.437185</td></tr><tr><td>933.7057925</td></tr><tr><td>920.4967705</td></tr><tr><td>909.5693409</td></tr><tr><td>897.0465147</td></tr><tr><td>884.4440656</td></tr><tr><td>888.6801555</td></tr><tr><td>879.2400453</td></tr><tr><td>867.1186603</td></tr><tr><td>870.0634374</td></tr><tr><td>892.364888</td></tr><tr><td>880.9312381</td></tr><tr><td>871.3117786</td></tr><tr><td>893.0221418</td></tr><tr><td>916.1102815</td></tr><tr><td>904.5961527</td></tr><tr><td>892.6420615</td></tr><tr><td>897.5143327</td></tr><tr><td>898.0384918</td></tr><tr><td>887.7455088</td></tr><tr><td>908.3223305</td></tr><tr><td>897.4882383</td></tr><tr><td>887.0388245</td></tr><tr><td>877.3773574</td></tr><tr><td>865.8804839</td></tr><tr><td>868.9462139</td></tr><tr><td>875.0141916</td></tr><tr><td>866.2581202</td></tr><tr><td>857.1021804</td></tr><tr><td>848.2435304</td></tr><tr><td>836.9054042</td></tr><tr><td>858.2465871</td></tr><tr><td>879.0791764</td></tr><tr><td>886.0698818</td></tr><tr><td>875.3899783</td></tr><tr><td>898.6773628</td></tr><tr><td>889.2201579</td></tr><tr><td>895.2892317</td></tr><tr><td>885.2927007</td></tr><tr><td>872.2541967</td></tr><tr><td>892.5651384</td></tr></table>"
                    },
                    "metadata": {
                        "azdata_chartOptions": {
                            "type": "bar",
                            "dataDirection": "horizontal",
                            "columnsAsLabels": true,
                            "labelFirstColumn": false,
                            "legendPosition": "none"
                        }
                    }
                }
            ],
            "execution_count": 39
        },
        {
            "cell_type": "markdown",
            "source": [
                "Sean actually holds the 24 lowest ratings in league history... yikes"
            ],
            "metadata": {
                "azdata_cell_guid": "3b301fac-189c-4492-bb68-f230804251ac"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, week_of_season, season \r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr \r\n",
                "LIMIT 25"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "d6d91b16-48aa-4ef2-ba60-92905e8b2e57"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(25 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.006"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 55,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Sean",
                                    "1": "836.9054042",
                                    "2": "6",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "848.2435304",
                                    "2": "5",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "857.1021804",
                                    "2": "4",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "858.2465871",
                                    "2": "7",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "865.8804839",
                                    "2": "16",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "866.2581202",
                                    "2": "3",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "867.1186603",
                                    "2": "15",
                                    "3": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "868.9462139",
                                    "2": "1",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "870.0634374",
                                    "2": "1",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "871.3117786",
                                    "2": "4",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "872.2541967",
                                    "2": "15",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "875.0141916",
                                    "2": "2",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "875.3899783",
                                    "2": "10",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "877.3773574",
                                    "2": "15",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "879.0791764",
                                    "2": "8",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "879.2400453",
                                    "2": "14",
                                    "3": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "880.9312381",
                                    "2": "3",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "884.4440656",
                                    "2": "12",
                                    "3": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "885.2927007",
                                    "2": "14",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "886.0698818",
                                    "2": "9",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "887.0388245",
                                    "2": "14",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "887.7455088",
                                    "2": "11",
                                    "3": "2021"
                                },
                                {
                                    "0": "Sean",
                                    "1": "888.6801555",
                                    "2": "13",
                                    "3": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "889.2201579",
                                    "2": "12",
                                    "3": "2022"
                                },
                                {
                                    "0": "Shev",
                                    "1": "890.6621515",
                                    "2": "14",
                                    "3": "2022"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>week_of_season</th><th>season</th></tr><tr><td>Sean</td><td>836.9054042</td><td>6</td><td>2022</td></tr><tr><td>Sean</td><td>848.2435304</td><td>5</td><td>2022</td></tr><tr><td>Sean</td><td>857.1021804</td><td>4</td><td>2022</td></tr><tr><td>Sean</td><td>858.2465871</td><td>7</td><td>2022</td></tr><tr><td>Sean</td><td>865.8804839</td><td>16</td><td>2021</td></tr><tr><td>Sean</td><td>866.2581202</td><td>3</td><td>2022</td></tr><tr><td>Sean</td><td>867.1186603</td><td>15</td><td>2020</td></tr><tr><td>Sean</td><td>868.9462139</td><td>1</td><td>2022</td></tr><tr><td>Sean</td><td>870.0634374</td><td>1</td><td>2021</td></tr><tr><td>Sean</td><td>871.3117786</td><td>4</td><td>2021</td></tr><tr><td>Sean</td><td>872.2541967</td><td>15</td><td>2022</td></tr><tr><td>Sean</td><td>875.0141916</td><td>2</td><td>2022</td></tr><tr><td>Sean</td><td>875.3899783</td><td>10</td><td>2022</td></tr><tr><td>Sean</td><td>877.3773574</td><td>15</td><td>2021</td></tr><tr><td>Sean</td><td>879.0791764</td><td>8</td><td>2022</td></tr><tr><td>Sean</td><td>879.2400453</td><td>14</td><td>2020</td></tr><tr><td>Sean</td><td>880.9312381</td><td>3</td><td>2021</td></tr><tr><td>Sean</td><td>884.4440656</td><td>12</td><td>2020</td></tr><tr><td>Sean</td><td>885.2927007</td><td>14</td><td>2022</td></tr><tr><td>Sean</td><td>886.0698818</td><td>9</td><td>2022</td></tr><tr><td>Sean</td><td>887.0388245</td><td>14</td><td>2021</td></tr><tr><td>Sean</td><td>887.7455088</td><td>11</td><td>2021</td></tr><tr><td>Sean</td><td>888.6801555</td><td>13</td><td>2020</td></tr><tr><td>Sean</td><td>889.2201579</td><td>12</td><td>2022</td></tr><tr><td>Shev</td><td>890.6621515</td><td>14</td><td>2022</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 55
        },
        {
            "cell_type": "markdown",
            "source": [
                "**Now let's take a look at the highest rating:**"
            ],
            "metadata": {
                "azdata_cell_guid": "488d723c-700a-4af1-ba81-7f7092b6a754"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, week_of_season, season \r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr DESC \r\n",
                "LIMIT 1"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "53aab1a2-9b4c-4f96-85df-d6eca1aaf412",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(1 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.004"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 4,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Loof",
                                    "1": "1138.030319",
                                    "2": "17",
                                    "3": "2021"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>week_of_season</th><th>season</th></tr><tr><td>Loof</td><td>1138.030319</td><td>17</td><td>2021</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 4
        },
        {
            "cell_type": "markdown",
            "source": [
                "Coming of a 2020 championship, Loof stayed hot and hit his peak at the very end of the 2021 season gaining over 50 rating points in the final 5 weeks to reach a league record 1138 rating. Unfortunatly, Loof failed to repeat as he ended up losing the\n",
                "\n",
                "the championship matchup to John."
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "cbb06b22-59dc-40cb-b144-38c987ec4999"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, score, opponent, opponent_ffmr, winner, week_of_season, season\r\n",
                "FROM elo.timeline\r\n",
                "WHERE team = \"Loof\" and season = '2021'"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "a0c1ef10-e2b5-435f-a559-bb9c98c0ba6d"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(17 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.005"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 44,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "score"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "winner"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Loof",
                                    "1": "1126.672835",
                                    "2": "96.5",
                                    "3": "Shev",
                                    "4": "973.6575368",
                                    "5": "Shev",
                                    "6": "1",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1104.510694",
                                    "2": "99.56",
                                    "3": "Nate",
                                    "4": "948.7199719",
                                    "5": "Nate",
                                    "6": "2",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1083.186308",
                                    "2": "143.62",
                                    "3": "Sean",
                                    "4": "880.9312381",
                                    "5": "Loof",
                                    "6": "3",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1093.826834",
                                    "2": "102.02",
                                    "3": "John",
                                    "4": "1108.05934",
                                    "5": "John",
                                    "6": "4",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1076.065872",
                                    "2": "149.5",
                                    "3": "Justin",
                                    "4": "956.6146724",
                                    "5": "Loof",
                                    "6": "5",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1086.92981",
                                    "2": "137.62",
                                    "3": "Eddie",
                                    "4": "1034.748908",
                                    "5": "Loof",
                                    "6": "6",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1099.078835",
                                    "2": "126.36",
                                    "3": "Derek",
                                    "4": "1010.526906",
                                    "5": "Derek",
                                    "6": "7",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1097.031411",
                                    "2": "143.96",
                                    "3": "Nick",
                                    "4": "1115.326439",
                                    "5": "Loof",
                                    "6": "8",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1110.738442",
                                    "2": "99.66",
                                    "3": "Pfeff",
                                    "4": "978.3905395",
                                    "5": "Pfeff",
                                    "6": "9",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1088.928661",
                                    "2": "123.94",
                                    "3": "Shev",
                                    "4": "967.9345236",
                                    "5": "Loof",
                                    "6": "10",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1100.805947",
                                    "2": "121.06",
                                    "3": "Nate",
                                    "4": "996.2688854",
                                    "5": "Nate",
                                    "6": "11",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1081.408355",
                                    "2": "135.0",
                                    "3": "Sean",
                                    "4": "908.3223305",
                                    "5": "Loof",
                                    "6": "12",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1092.428266",
                                    "2": "123.8",
                                    "3": "John",
                                    "4": "1085.055321",
                                    "5": "Loof",
                                    "6": "13",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1106.14505",
                                    "2": "134.92",
                                    "3": "Justin",
                                    "4": "954.6775339",
                                    "5": "Loof",
                                    "6": "14",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1115.845959",
                                    "2": "99.2",
                                    "3": "Pfeff",
                                    "4": "969.6106143",
                                    "5": "Loof",
                                    "6": "15",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1126.096667",
                                    "2": "122.46",
                                    "3": "Nate",
                                    "4": "1018.427868",
                                    "5": "Loof",
                                    "6": "16",
                                    "7": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1138.030319",
                                    "2": "130.8",
                                    "3": "John",
                                    "4": "1098.298588",
                                    "5": "John",
                                    "6": "17",
                                    "7": "2021"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>score</th><th>opponent</th><th>opponent_ffmr</th><th>winner</th><th>week_of_season</th><th>season</th></tr><tr><td>Loof</td><td>1126.672835</td><td>96.5</td><td>Shev</td><td>973.6575368</td><td>Shev</td><td>1</td><td>2021</td></tr><tr><td>Loof</td><td>1104.510694</td><td>99.56</td><td>Nate</td><td>948.7199719</td><td>Nate</td><td>2</td><td>2021</td></tr><tr><td>Loof</td><td>1083.186308</td><td>143.62</td><td>Sean</td><td>880.9312381</td><td>Loof</td><td>3</td><td>2021</td></tr><tr><td>Loof</td><td>1093.826834</td><td>102.02</td><td>John</td><td>1108.05934</td><td>John</td><td>4</td><td>2021</td></tr><tr><td>Loof</td><td>1076.065872</td><td>149.5</td><td>Justin</td><td>956.6146724</td><td>Loof</td><td>5</td><td>2021</td></tr><tr><td>Loof</td><td>1086.92981</td><td>137.62</td><td>Eddie</td><td>1034.748908</td><td>Loof</td><td>6</td><td>2021</td></tr><tr><td>Loof</td><td>1099.078835</td><td>126.36</td><td>Derek</td><td>1010.526906</td><td>Derek</td><td>7</td><td>2021</td></tr><tr><td>Loof</td><td>1097.031411</td><td>143.96</td><td>Nick</td><td>1115.326439</td><td>Loof</td><td>8</td><td>2021</td></tr><tr><td>Loof</td><td>1110.738442</td><td>99.66</td><td>Pfeff</td><td>978.3905395</td><td>Pfeff</td><td>9</td><td>2021</td></tr><tr><td>Loof</td><td>1088.928661</td><td>123.94</td><td>Shev</td><td>967.9345236</td><td>Loof</td><td>10</td><td>2021</td></tr><tr><td>Loof</td><td>1100.805947</td><td>121.06</td><td>Nate</td><td>996.2688854</td><td>Nate</td><td>11</td><td>2021</td></tr><tr><td>Loof</td><td>1081.408355</td><td>135.0</td><td>Sean</td><td>908.3223305</td><td>Loof</td><td>12</td><td>2021</td></tr><tr><td>Loof</td><td>1092.428266</td><td>123.8</td><td>John</td><td>1085.055321</td><td>Loof</td><td>13</td><td>2021</td></tr><tr><td>Loof</td><td>1106.14505</td><td>134.92</td><td>Justin</td><td>954.6775339</td><td>Loof</td><td>14</td><td>2021</td></tr><tr><td>Loof</td><td>1115.845959</td><td>99.2</td><td>Pfeff</td><td>969.6106143</td><td>Loof</td><td>15</td><td>2021</td></tr><tr><td>Loof</td><td>1126.096667</td><td>122.46</td><td>Nate</td><td>1018.427868</td><td>Loof</td><td>16</td><td>2021</td></tr><tr><td>Loof</td><td>1138.030319</td><td>130.8</td><td>John</td><td>1098.298588</td><td>John</td><td>17</td><td>2021</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 44
        },
        {
            "cell_type": "markdown",
            "source": [
                "Loof's rating: (he entered the league in 2020 so his graph is a bit smaller than Sean's)"
            ],
            "metadata": {
                "azdata_cell_guid": "9a0bf8ae-2790-44cf-848f-cf07990bc63f"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT ffmr\r\n",
                "FROM elo.timeline\r\n",
                "WHERE team = \"Loof\""
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "f1b714e4-a10f-4da8-aa18-0014a0322cf2"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(48 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.006"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 30,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "ffmr"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "1000.0"
                                },
                                {
                                    "0": "1014.817261"
                                },
                                {
                                    "0": "1031.564491"
                                },
                                {
                                    "0": "1046.432341"
                                },
                                {
                                    "0": "1045.459748"
                                },
                                {
                                    "0": "1059.731065"
                                },
                                {
                                    "0": "1073.623999"
                                },
                                {
                                    "0": "1055.298764"
                                },
                                {
                                    "0": "1068.096245"
                                },
                                {
                                    "0": "1081.213006"
                                },
                                {
                                    "0": "1092.63323"
                                },
                                {
                                    "0": "1091.105741"
                                },
                                {
                                    "0": "1102.517452"
                                },
                                {
                                    "0": "1120.063231"
                                },
                                {
                                    "0": "1131.812677"
                                },
                                {
                                    "0": "1126.672835"
                                },
                                {
                                    "0": "1104.510694"
                                },
                                {
                                    "0": "1083.186308"
                                },
                                {
                                    "0": "1093.826834"
                                },
                                {
                                    "0": "1076.065872"
                                },
                                {
                                    "0": "1086.92981"
                                },
                                {
                                    "0": "1099.078835"
                                },
                                {
                                    "0": "1097.031411"
                                },
                                {
                                    "0": "1110.738442"
                                },
                                {
                                    "0": "1088.928661"
                                },
                                {
                                    "0": "1100.805947"
                                },
                                {
                                    "0": "1081.408355"
                                },
                                {
                                    "0": "1092.428266"
                                },
                                {
                                    "0": "1106.14505"
                                },
                                {
                                    "0": "1115.845959"
                                },
                                {
                                    "0": "1126.096667"
                                },
                                {
                                    "0": "1138.030319"
                                },
                                {
                                    "0": "1119.62927"
                                },
                                {
                                    "0": "1129.54885"
                                },
                                {
                                    "0": "1120.997976"
                                },
                                {
                                    "0": "1100.306926"
                                },
                                {
                                    "0": "1081.845423"
                                },
                                {
                                    "0": "1060.802083"
                                },
                                {
                                    "0": "1075.915645"
                                },
                                {
                                    "0": "1089.049008"
                                },
                                {
                                    "0": "1084.182904"
                                },
                                {
                                    "0": "1095.431819"
                                },
                                {
                                    "0": "1088.613889"
                                },
                                {
                                    "0": "1081.74366"
                                },
                                {
                                    "0": "1063.17003"
                                },
                                {
                                    "0": "1063.855908"
                                },
                                {
                                    "0": "1075.393828"
                                },
                                {
                                    "0": "1057.22446"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>ffmr</th></tr><tr><td>1000.0</td></tr><tr><td>1014.817261</td></tr><tr><td>1031.564491</td></tr><tr><td>1046.432341</td></tr><tr><td>1045.459748</td></tr><tr><td>1059.731065</td></tr><tr><td>1073.623999</td></tr><tr><td>1055.298764</td></tr><tr><td>1068.096245</td></tr><tr><td>1081.213006</td></tr><tr><td>1092.63323</td></tr><tr><td>1091.105741</td></tr><tr><td>1102.517452</td></tr><tr><td>1120.063231</td></tr><tr><td>1131.812677</td></tr><tr><td>1126.672835</td></tr><tr><td>1104.510694</td></tr><tr><td>1083.186308</td></tr><tr><td>1093.826834</td></tr><tr><td>1076.065872</td></tr><tr><td>1086.92981</td></tr><tr><td>1099.078835</td></tr><tr><td>1097.031411</td></tr><tr><td>1110.738442</td></tr><tr><td>1088.928661</td></tr><tr><td>1100.805947</td></tr><tr><td>1081.408355</td></tr><tr><td>1092.428266</td></tr><tr><td>1106.14505</td></tr><tr><td>1115.845959</td></tr><tr><td>1126.096667</td></tr><tr><td>1138.030319</td></tr><tr><td>1119.62927</td></tr><tr><td>1129.54885</td></tr><tr><td>1120.997976</td></tr><tr><td>1100.306926</td></tr><tr><td>1081.845423</td></tr><tr><td>1060.802083</td></tr><tr><td>1075.915645</td></tr><tr><td>1089.049008</td></tr><tr><td>1084.182904</td></tr><tr><td>1095.431819</td></tr><tr><td>1088.613889</td></tr><tr><td>1081.74366</td></tr><tr><td>1063.17003</td></tr><tr><td>1063.855908</td></tr><tr><td>1075.393828</td></tr><tr><td>1057.22446</td></tr></table>"
                    },
                    "metadata": {
                        "azdata_chartOptions": {
                            "type": "bar",
                            "dataDirection": "horizontal",
                            "columnsAsLabels": true,
                            "labelFirstColumn": false,
                            "legendPosition": "none",
                            "yAxisMin": 900,
                            "yAxisMax": 1200
                        }
                    }
                }
            ],
            "execution_count": 30
        },
        {
            "cell_type": "markdown",
            "source": [
                "Some other top ratings:"
            ],
            "metadata": {
                "azdata_cell_guid": "c0480ea6-71e8-48f8-8244-4f52cc09cef3"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, week_of_season, season \r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr DESC \r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "azdata_cell_guid": "437eb6e2-4476-4c52-b0ad-693d75651bb1",
                "language": "sql"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.013"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 51,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Loof",
                                    "1": "1138.030319",
                                    "2": "17",
                                    "3": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1131.812677",
                                    "2": "16",
                                    "3": "2020"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1129.54885",
                                    "2": "2",
                                    "3": "2022"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1126.672835",
                                    "2": "1",
                                    "3": "2021"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1126.096667",
                                    "2": "16",
                                    "3": "2021"
                                },
                                {
                                    "0": "John",
                                    "1": "1123.640596",
                                    "2": "16",
                                    "3": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "1121.409774",
                                    "2": "13",
                                    "3": "2018"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1120.997976",
                                    "2": "3",
                                    "3": "2022"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1120.063231",
                                    "2": "15",
                                    "3": "2020"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1119.62927",
                                    "2": "1",
                                    "3": "2022"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>week_of_season</th><th>season</th></tr><tr><td>Loof</td><td>1138.030319</td><td>17</td><td>2021</td></tr><tr><td>Loof</td><td>1131.812677</td><td>16</td><td>2020</td></tr><tr><td>Loof</td><td>1129.54885</td><td>2</td><td>2022</td></tr><tr><td>Loof</td><td>1126.672835</td><td>1</td><td>2021</td></tr><tr><td>Loof</td><td>1126.096667</td><td>16</td><td>2021</td></tr><tr><td>John</td><td>1123.640596</td><td>16</td><td>2022</td></tr><tr><td>Sean</td><td>1121.409774</td><td>13</td><td>2018</td></tr><tr><td>Loof</td><td>1120.997976</td><td>3</td><td>2022</td></tr><tr><td>Loof</td><td>1120.063231</td><td>15</td><td>2020</td></tr><tr><td>Loof</td><td>1119.62927</td><td>1</td><td>2022</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 51
        },
        {
            "cell_type": "markdown",
            "source": [
                "**Notable Matchups (Matchups are displayed twice, sorry it doesn't look very nice)**"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "1342a370-b0a1-463b-ab9c-9e1c35a2b2b7"
            },
            "attachments": {}
        },
        {
            "cell_type": "markdown",
            "source": [
                "Here are the top 5 matchups with the highest combined ratings. The aforementioned 2021 championship game tops the list, which shouldn't be too surprising. Note that Loof is in every single one of them and that 3 of the 5 are matchups between \n",
                "\n",
                "Loof and John. It's also interesting to note that John beat Loof all 3 times."
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "eceff31d-f323-4484-830e-ba26b3774b14"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, opponent, opponent_ffmr, week_of_season, season, winner\r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr + opponent_ffmr DESC \r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "68549941-40f3-4454-823b-fe0699f342b3",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.012"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 52,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    },
                                    {
                                        "name": "winner"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "John",
                                    "1": "1098.298588",
                                    "2": "Loof",
                                    "3": "1138.030319",
                                    "4": "17",
                                    "5": "2021",
                                    "6": "John"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1138.030319",
                                    "2": "John",
                                    "3": "1098.298588",
                                    "4": "17",
                                    "5": "2021",
                                    "6": "John"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1097.031411",
                                    "2": "Nick",
                                    "3": "1115.326439",
                                    "4": "8",
                                    "5": "2021",
                                    "6": "Loof"
                                },
                                {
                                    "0": "Nick",
                                    "1": "1115.326439",
                                    "2": "Loof",
                                    "3": "1097.031411",
                                    "4": "8",
                                    "5": "2021",
                                    "6": "Loof"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "1087.227376",
                                    "2": "Loof",
                                    "3": "1120.063231",
                                    "4": "15",
                                    "5": "2020",
                                    "6": "Loof"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1120.063231",
                                    "2": "Eddie",
                                    "3": "1087.227376",
                                    "4": "15",
                                    "5": "2020",
                                    "6": "Loof"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1093.826834",
                                    "2": "John",
                                    "3": "1108.05934",
                                    "4": "4",
                                    "5": "2021",
                                    "6": "John"
                                },
                                {
                                    "0": "John",
                                    "1": "1108.05934",
                                    "2": "Loof",
                                    "3": "1093.826834",
                                    "4": "4",
                                    "5": "2021",
                                    "6": "John"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1100.306926",
                                    "2": "John",
                                    "3": "1100.527304",
                                    "4": "4",
                                    "5": "2022",
                                    "6": "John"
                                },
                                {
                                    "0": "John",
                                    "1": "1100.527304",
                                    "2": "Loof",
                                    "3": "1100.306926",
                                    "4": "4",
                                    "5": "2022",
                                    "6": "John"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>opponent</th><th>opponent_ffmr</th><th>week_of_season</th><th>season</th><th>winner</th></tr><tr><td>John</td><td>1098.298588</td><td>Loof</td><td>1138.030319</td><td>17</td><td>2021</td><td>John</td></tr><tr><td>Loof</td><td>1138.030319</td><td>John</td><td>1098.298588</td><td>17</td><td>2021</td><td>John</td></tr><tr><td>Loof</td><td>1097.031411</td><td>Nick</td><td>1115.326439</td><td>8</td><td>2021</td><td>Loof</td></tr><tr><td>Nick</td><td>1115.326439</td><td>Loof</td><td>1097.031411</td><td>8</td><td>2021</td><td>Loof</td></tr><tr><td>Eddie</td><td>1087.227376</td><td>Loof</td><td>1120.063231</td><td>15</td><td>2020</td><td>Loof</td></tr><tr><td>Loof</td><td>1120.063231</td><td>Eddie</td><td>1087.227376</td><td>15</td><td>2020</td><td>Loof</td></tr><tr><td>Loof</td><td>1093.826834</td><td>John</td><td>1108.05934</td><td>4</td><td>2021</td><td>John</td></tr><tr><td>John</td><td>1108.05934</td><td>Loof</td><td>1093.826834</td><td>4</td><td>2021</td><td>John</td></tr><tr><td>Loof</td><td>1100.306926</td><td>John</td><td>1100.527304</td><td>4</td><td>2022</td><td>John</td></tr><tr><td>John</td><td>1100.527304</td><td>Loof</td><td>1100.306926</td><td>4</td><td>2022</td><td>John</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 52
        },
        {
            "cell_type": "markdown",
            "source": [
                "Now let's take a look at the biggest stinkers, all featuring Sean (of course). I won't even show the winners becuase who really cares."
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "8057fa66-7edf-489e-9775-9751cd62c89d"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, opponent, opponent_ffmr, week_of_season, season\r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr + opponent_ffmr\r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "09fac4e6-cd95-4a4f-8857-61b2541bbeae"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.017"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 57,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Shev",
                                    "1": "923.9621109",
                                    "2": "Sean",
                                    "3": "848.2435304",
                                    "4": "5",
                                    "5": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "848.2435304",
                                    "2": "Shev",
                                    "3": "923.9621109",
                                    "4": "5",
                                    "5": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "836.9054042",
                                    "2": "Justin",
                                    "3": "936.805472",
                                    "4": "6",
                                    "5": "2022"
                                },
                                {
                                    "0": "Justin",
                                    "1": "936.805472",
                                    "2": "Sean",
                                    "3": "836.9054042",
                                    "4": "6",
                                    "5": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "885.2927007",
                                    "2": "Shev",
                                    "3": "890.6621515",
                                    "4": "14",
                                    "5": "2022"
                                },
                                {
                                    "0": "Shev",
                                    "1": "890.6621515",
                                    "2": "Sean",
                                    "3": "885.2927007",
                                    "4": "14",
                                    "5": "2022"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "929.1462149",
                                    "2": "Sean",
                                    "3": "858.2465871",
                                    "4": "7",
                                    "5": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "858.2465871",
                                    "2": "Pfeff",
                                    "3": "929.1462149",
                                    "4": "7",
                                    "5": "2022"
                                },
                                {
                                    "0": "Nate",
                                    "1": "922.764491",
                                    "2": "Sean",
                                    "3": "867.1186603",
                                    "4": "15",
                                    "5": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "867.1186603",
                                    "2": "Nate",
                                    "3": "922.764491",
                                    "4": "15",
                                    "5": "2020"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>opponent</th><th>opponent_ffmr</th><th>week_of_season</th><th>season</th></tr><tr><td>Shev</td><td>923.9621109</td><td>Sean</td><td>848.2435304</td><td>5</td><td>2022</td></tr><tr><td>Sean</td><td>848.2435304</td><td>Shev</td><td>923.9621109</td><td>5</td><td>2022</td></tr><tr><td>Sean</td><td>836.9054042</td><td>Justin</td><td>936.805472</td><td>6</td><td>2022</td></tr><tr><td>Justin</td><td>936.805472</td><td>Sean</td><td>836.9054042</td><td>6</td><td>2022</td></tr><tr><td>Sean</td><td>885.2927007</td><td>Shev</td><td>890.6621515</td><td>14</td><td>2022</td></tr><tr><td>Shev</td><td>890.6621515</td><td>Sean</td><td>885.2927007</td><td>14</td><td>2022</td></tr><tr><td>Pfeff</td><td>929.1462149</td><td>Sean</td><td>858.2465871</td><td>7</td><td>2022</td></tr><tr><td>Sean</td><td>858.2465871</td><td>Pfeff</td><td>929.1462149</td><td>7</td><td>2022</td></tr><tr><td>Nate</td><td>922.764491</td><td>Sean</td><td>867.1186603</td><td>15</td><td>2020</td></tr><tr><td>Sean</td><td>867.1186603</td><td>Nate</td><td>922.764491</td><td>15</td><td>2020</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 57
        },
        {
            "cell_type": "markdown",
            "source": [
                "Heres the matchups with the greatest rating disparities, all vs Sean (of course)."
            ],
            "metadata": {
                "azdata_cell_guid": "89efbc23-1705-4205-8a7d-d3c55b282a11"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, opponent, opponent_ffmr, week_of_season, season, winner\r\n",
                "FROM elo.timeline \r\n",
                "ORDER BY ffmr - opponent_ffmr DESC\r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "5b013695-e54a-45e2-8ccf-db6cdd1de4c0",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.015"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 11,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    },
                                    {
                                        "name": "winner"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Loof",
                                    "1": "1129.54885",
                                    "2": "Sean",
                                    "3": "875.0141916",
                                    "4": "2",
                                    "5": "2022",
                                    "6": "Loof"
                                },
                                {
                                    "0": "John",
                                    "1": "1099.323164",
                                    "2": "Sean",
                                    "3": "868.9462139",
                                    "4": "1",
                                    "5": "2022",
                                    "6": "Sean"
                                },
                                {
                                    "0": "Nick",
                                    "1": "1095.120116",
                                    "2": "Sean",
                                    "3": "866.2581202",
                                    "4": "3",
                                    "5": "2022",
                                    "6": "Nick"
                                },
                                {
                                    "0": "John",
                                    "1": "1088.939854",
                                    "2": "Sean",
                                    "3": "875.3899783",
                                    "4": "10",
                                    "5": "2022",
                                    "6": "Sean"
                                },
                                {
                                    "0": "John",
                                    "1": "1103.230695",
                                    "2": "Sean",
                                    "3": "893.0221418",
                                    "4": "5",
                                    "5": "2021",
                                    "6": "Sean"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1083.186308",
                                    "2": "Sean",
                                    "3": "880.9312381",
                                    "4": "3",
                                    "5": "2021",
                                    "6": "Loof"
                                },
                                {
                                    "0": "John",
                                    "1": "1086.615893",
                                    "2": "Sean",
                                    "3": "888.6801555",
                                    "4": "13",
                                    "5": "2020",
                                    "6": "John"
                                },
                                {
                                    "0": "Nate",
                                    "1": "1051.860391",
                                    "2": "Sean",
                                    "3": "857.1021804",
                                    "4": "4",
                                    "5": "2022",
                                    "6": "Nate"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1088.613889",
                                    "2": "Sean",
                                    "3": "898.6773628",
                                    "4": "11",
                                    "5": "2022",
                                    "6": "Loof"
                                },
                                {
                                    "0": "Nick",
                                    "1": "1057.626097",
                                    "2": "Sean",
                                    "3": "870.0634374",
                                    "4": "1",
                                    "5": "2021",
                                    "6": "Sean"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>opponent</th><th>opponent_ffmr</th><th>week_of_season</th><th>season</th><th>winner</th></tr><tr><td>Loof</td><td>1129.54885</td><td>Sean</td><td>875.0141916</td><td>2</td><td>2022</td><td>Loof</td></tr><tr><td>John</td><td>1099.323164</td><td>Sean</td><td>868.9462139</td><td>1</td><td>2022</td><td>Sean</td></tr><tr><td>Nick</td><td>1095.120116</td><td>Sean</td><td>866.2581202</td><td>3</td><td>2022</td><td>Nick</td></tr><tr><td>John</td><td>1088.939854</td><td>Sean</td><td>875.3899783</td><td>10</td><td>2022</td><td>Sean</td></tr><tr><td>John</td><td>1103.230695</td><td>Sean</td><td>893.0221418</td><td>5</td><td>2021</td><td>Sean</td></tr><tr><td>Loof</td><td>1083.186308</td><td>Sean</td><td>880.9312381</td><td>3</td><td>2021</td><td>Loof</td></tr><tr><td>John</td><td>1086.615893</td><td>Sean</td><td>888.6801555</td><td>13</td><td>2020</td><td>John</td></tr><tr><td>Nate</td><td>1051.860391</td><td>Sean</td><td>857.1021804</td><td>4</td><td>2022</td><td>Nate</td></tr><tr><td>Loof</td><td>1088.613889</td><td>Sean</td><td>898.6773628</td><td>11</td><td>2022</td><td>Loof</td></tr><tr><td>Nick</td><td>1057.626097</td><td>Sean</td><td>870.0634374</td><td>1</td><td>2021</td><td>Sean</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 11
        },
        {
            "cell_type": "markdown",
            "source": [
                "**Ratings by team**"
            ],
            "metadata": {
                "language": "",
                "azdata_cell_guid": "382f06dc-96cc-47a3-9977-fc2f709caa05"
            },
            "attachments": {}
        },
        {
            "cell_type": "markdown",
            "source": [
                "Let's take a look at the ratings for each manager. Note that the top 4 teams in terms of average rating are the 4 teams with championships and that Sean's actually not last for once."
            ],
            "metadata": {
                "azdata_cell_guid": "60b9db6a-3e4a-41bb-b59c-c1ac8e1317f8"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, AVG(ffmr), MIN(ffmr), MAX(ffmr)\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team \r\n",
                "ORDER BY AVG(ffmr) DESC"
            ],
            "metadata": {
                "azdata_cell_guid": "5b8a3018-4d22-46ef-8cab-cd29ab239e2f",
                "language": "sql",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(13 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.010"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 62,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "AVG(ffmr)"
                                    },
                                    {
                                        "name": "MIN(ffmr)"
                                    },
                                    {
                                        "name": "MAX(ffmr)"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Loof",
                                    "1": "1086.0377332291664",
                                    "2": "1000.0",
                                    "3": "1138.030319"
                                },
                                {
                                    "0": "John",
                                    "1": "1079.0640460657894",
                                    "2": "1016.0",
                                    "3": "1123.640596"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "1032.1394608050002",
                                    "2": "995.6201383",
                                    "3": "1087.227376"
                                },
                                {
                                    "0": "Nick",
                                    "1": "1022.7993069683544",
                                    "2": "946.6285413",
                                    "3": "1115.326439"
                                },
                                {
                                    "0": "Derek",
                                    "1": "999.8766791513159",
                                    "2": "927.4672248",
                                    "3": "1103.420452"
                                },
                                {
                                    "0": "Nate",
                                    "1": "999.0650543118419",
                                    "2": "922.764491",
                                    "3": "1105.636317"
                                },
                                {
                                    "0": "Justin",
                                    "1": "988.9432105467531",
                                    "2": "907.0313124",
                                    "3": "1081.004377"
                                },
                                {
                                    "0": "Pete",
                                    "1": "983.7882646896553",
                                    "2": "947.0093265",
                                    "3": "1022.85791"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "978.2573317961038",
                                    "2": "897.5775829",
                                    "3": "1027.866558"
                                },
                                {
                                    "0": "Zach",
                                    "1": "974.231015775",
                                    "2": "939.0184708",
                                    "3": "1016.0"
                                },
                                {
                                    "0": "Sean",
                                    "1": "954.9696622026311",
                                    "2": "836.9054042",
                                    "3": "1121.409774"
                                },
                                {
                                    "0": "James",
                                    "1": "953.4395054800001",
                                    "2": "907.3629625",
                                    "3": "1001.4016"
                                },
                                {
                                    "0": "Shev",
                                    "1": "953.1638438246757",
                                    "2": "890.6621515",
                                    "3": "991.1617073"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>AVG(ffmr)</th><th>MIN(ffmr)</th><th>MAX(ffmr)</th></tr><tr><td>Loof</td><td>1086.0377332291664</td><td>1000.0</td><td>1138.030319</td></tr><tr><td>John</td><td>1079.0640460657894</td><td>1016.0</td><td>1123.640596</td></tr><tr><td>Eddie</td><td>1032.1394608050002</td><td>995.6201383</td><td>1087.227376</td></tr><tr><td>Nick</td><td>1022.7993069683544</td><td>946.6285413</td><td>1115.326439</td></tr><tr><td>Derek</td><td>999.8766791513159</td><td>927.4672248</td><td>1103.420452</td></tr><tr><td>Nate</td><td>999.0650543118419</td><td>922.764491</td><td>1105.636317</td></tr><tr><td>Justin</td><td>988.9432105467531</td><td>907.0313124</td><td>1081.004377</td></tr><tr><td>Pete</td><td>983.7882646896553</td><td>947.0093265</td><td>1022.85791</td></tr><tr><td>Pfeff</td><td>978.2573317961038</td><td>897.5775829</td><td>1027.866558</td></tr><tr><td>Zach</td><td>974.231015775</td><td>939.0184708</td><td>1016.0</td></tr><tr><td>Sean</td><td>954.9696622026311</td><td>836.9054042</td><td>1121.409774</td></tr><tr><td>James</td><td>953.4395054800001</td><td>907.3629625</td><td>1001.4016</td></tr><tr><td>Shev</td><td>953.1638438246757</td><td>890.6621515</td><td>991.1617073</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 62
        },
        {
            "cell_type": "markdown",
            "source": [
                "Now let's look at the most volitile seasons, the direction of the rating in these is not explicit, but can be inferred in some cases."
            ],
            "metadata": {
                "language": "",
                "azdata_cell_guid": "9d2217c0-2283-42f8-a90f-37cc9ad5fab7"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, MIN(ffmr), MAX(ffmr), MAX(ffmr) - MIN(ffmr), season\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team, season\r\n",
                "ORDER BY MAX(ffmr) - MIN(ffmr) DESC\r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "azdata_cell_guid": "a7474022-faeb-4e9f-a84b-0b248726079c",
                "language": "sql",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.004"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 26,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "MIN(ffmr)"
                                    },
                                    {
                                        "name": "MAX(ffmr)"
                                    },
                                    {
                                        "name": "MAX(ffmr) - MIN(ffmr)"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Derek",
                                    "1": "966.8393456",
                                    "2": "1103.420452",
                                    "3": "136.58110640000007",
                                    "4": "2022"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1000.0",
                                    "2": "1131.812677",
                                    "3": "131.8126769999999",
                                    "4": "2020"
                                },
                                {
                                    "0": "Sean",
                                    "1": "867.1186603",
                                    "2": "987.6894973",
                                    "3": "120.57083699999998",
                                    "4": "2020"
                                },
                                {
                                    "0": "Nick",
                                    "1": "999.1441087",
                                    "2": "1105.137995",
                                    "3": "105.9938863000001",
                                    "4": "2022"
                                },
                                {
                                    "0": "Sean",
                                    "1": "1016.0",
                                    "2": "1121.409774",
                                    "3": "105.40977399999997",
                                    "4": "2018"
                                },
                                {
                                    "0": "Nate",
                                    "1": "954.8916597",
                                    "2": "1058.60637",
                                    "3": "103.71471029999998",
                                    "4": "2018"
                                },
                                {
                                    "0": "Nate",
                                    "1": "922.764491",
                                    "2": "1020.253362",
                                    "3": "97.48887100000002",
                                    "4": "2020"
                                },
                                {
                                    "0": "James",
                                    "1": "907.3629625",
                                    "2": "1001.4016",
                                    "3": "94.03863750000005",
                                    "4": "2019"
                                },
                                {
                                    "0": "Justin",
                                    "1": "907.0313124",
                                    "2": "999.4709882",
                                    "3": "92.43967579999992",
                                    "4": "2021"
                                },
                                {
                                    "0": "Justin",
                                    "1": "991.8485601",
                                    "2": "1081.004377",
                                    "3": "89.15581689999999",
                                    "4": "2019"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>MIN(ffmr)</th><th>MAX(ffmr)</th><th>MAX(ffmr) - MIN(ffmr)</th><th>season</th></tr><tr><td>Derek</td><td>966.8393456</td><td>1103.420452</td><td>136.58110640000007</td><td>2022</td></tr><tr><td>Loof</td><td>1000.0</td><td>1131.812677</td><td>131.8126769999999</td><td>2020</td></tr><tr><td>Sean</td><td>867.1186603</td><td>987.6894973</td><td>120.57083699999998</td><td>2020</td></tr><tr><td>Nick</td><td>999.1441087</td><td>1105.137995</td><td>105.9938863000001</td><td>2022</td></tr><tr><td>Sean</td><td>1016.0</td><td>1121.409774</td><td>105.40977399999997</td><td>2018</td></tr><tr><td>Nate</td><td>954.8916597</td><td>1058.60637</td><td>103.71471029999998</td><td>2018</td></tr><tr><td>Nate</td><td>922.764491</td><td>1020.253362</td><td>97.48887100000002</td><td>2020</td></tr><tr><td>James</td><td>907.3629625</td><td>1001.4016</td><td>94.03863750000005</td><td>2019</td></tr><tr><td>Justin</td><td>907.0313124</td><td>999.4709882</td><td>92.43967579999992</td><td>2021</td></tr><tr><td>Justin</td><td>991.8485601</td><td>1081.004377</td><td>89.15581689999999</td><td>2019</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 26
        },
        {
            "cell_type": "markdown",
            "source": [
                "I think Derek's 2022 season is worthy of a deeper inspection. Coming off a rough year in 2021, Derek started the year with a 966.84 rating and absolutely killed it. His only regular season loses came against 1070+ rated opponents and he consistantly \n",
                "\n",
                "put up high scores. He reached his peak rating at the championship game and ended up losing, which seems to be a common occurance. A great season nonetheless."
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "31a254e4-c140-412a-8e53-8b46b9fd924b"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, ffmr, score, opponent, opponent_ffmr, winner, week_of_season, season\r\n",
                "FROM elo.timeline\r\n",
                "WHERE team = \"Derek\" and season = '2022'"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "2c17b8c9-2765-4266-8868-7abb221a96d0"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(16 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.011"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 63,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "ffmr"
                                    },
                                    {
                                        "name": "score"
                                    },
                                    {
                                        "name": "opponent"
                                    },
                                    {
                                        "name": "opponent_ffmr"
                                    },
                                    {
                                        "name": "winner"
                                    },
                                    {
                                        "name": "week_of_season"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Derek",
                                    "1": "966.8393456",
                                    "2": "166.38",
                                    "3": "Nick",
                                    "4": "1086.126346",
                                    "5": "Derek",
                                    "6": "1",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "985.6368651",
                                    "2": "146.58",
                                    "3": "John",
                                    "4": "1077.016372",
                                    "5": "John",
                                    "6": "2",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "989.2765031",
                                    "2": "138.7",
                                    "3": "Justin",
                                    "4": "944.8651938",
                                    "5": "Derek",
                                    "6": "3",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1004.196916",
                                    "2": "152.02",
                                    "3": "Pfeff",
                                    "4": "936.1943462",
                                    "5": "Derek",
                                    "6": "4",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1018.812559",
                                    "2": "153.68",
                                    "3": "Eddie",
                                    "4": "1017.381627",
                                    "5": "Derek",
                                    "6": "5",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1034.874119",
                                    "2": "117.36",
                                    "3": "Nate",
                                    "4": "1079.037647",
                                    "5": "Nate",
                                    "6": "6",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1036.360742",
                                    "2": "103.54",
                                    "3": "Loof",
                                    "4": "1075.915645",
                                    "5": "Loof",
                                    "6": "7",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1020.102492",
                                    "2": "151.52",
                                    "3": "Sean",
                                    "4": "879.0791764",
                                    "5": "Derek",
                                    "6": "8",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1033.365593",
                                    "2": "134.9",
                                    "3": "Shev",
                                    "4": "932.057002",
                                    "5": "Derek",
                                    "6": "9",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1046.806708",
                                    "2": "120.3",
                                    "3": "Nick",
                                    "4": "1020.798901",
                                    "5": "Derek",
                                    "6": "10",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1061.12954",
                                    "2": "87.48",
                                    "3": "John",
                                    "4": "1084.447879",
                                    "5": "John",
                                    "6": "11",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1044.039491",
                                    "2": "148.26",
                                    "3": "Justin",
                                    "4": "987.0801425",
                                    "5": "Derek",
                                    "6": "12",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1056.868747",
                                    "2": "126.12",
                                    "3": "Pfeff",
                                    "4": "934.3839613",
                                    "5": "Derek",
                                    "6": "13",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1068.799009",
                                    "2": "166.38",
                                    "3": "Eddie",
                                    "4": "1043.339021",
                                    "5": "Derek",
                                    "6": "14",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1089.834797",
                                    "2": "143.08",
                                    "3": "Eddie",
                                    "4": "1025.980693",
                                    "5": "Derek",
                                    "6": "16",
                                    "7": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1103.420452",
                                    "2": "75.42",
                                    "3": "Nick",
                                    "4": "1034.582526",
                                    "5": "Nick",
                                    "6": "17",
                                    "7": "2022"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>ffmr</th><th>score</th><th>opponent</th><th>opponent_ffmr</th><th>winner</th><th>week_of_season</th><th>season</th></tr><tr><td>Derek</td><td>966.8393456</td><td>166.38</td><td>Nick</td><td>1086.126346</td><td>Derek</td><td>1</td><td>2022</td></tr><tr><td>Derek</td><td>985.6368651</td><td>146.58</td><td>John</td><td>1077.016372</td><td>John</td><td>2</td><td>2022</td></tr><tr><td>Derek</td><td>989.2765031</td><td>138.7</td><td>Justin</td><td>944.8651938</td><td>Derek</td><td>3</td><td>2022</td></tr><tr><td>Derek</td><td>1004.196916</td><td>152.02</td><td>Pfeff</td><td>936.1943462</td><td>Derek</td><td>4</td><td>2022</td></tr><tr><td>Derek</td><td>1018.812559</td><td>153.68</td><td>Eddie</td><td>1017.381627</td><td>Derek</td><td>5</td><td>2022</td></tr><tr><td>Derek</td><td>1034.874119</td><td>117.36</td><td>Nate</td><td>1079.037647</td><td>Nate</td><td>6</td><td>2022</td></tr><tr><td>Derek</td><td>1036.360742</td><td>103.54</td><td>Loof</td><td>1075.915645</td><td>Loof</td><td>7</td><td>2022</td></tr><tr><td>Derek</td><td>1020.102492</td><td>151.52</td><td>Sean</td><td>879.0791764</td><td>Derek</td><td>8</td><td>2022</td></tr><tr><td>Derek</td><td>1033.365593</td><td>134.9</td><td>Shev</td><td>932.057002</td><td>Derek</td><td>9</td><td>2022</td></tr><tr><td>Derek</td><td>1046.806708</td><td>120.3</td><td>Nick</td><td>1020.798901</td><td>Derek</td><td>10</td><td>2022</td></tr><tr><td>Derek</td><td>1061.12954</td><td>87.48</td><td>John</td><td>1084.447879</td><td>John</td><td>11</td><td>2022</td></tr><tr><td>Derek</td><td>1044.039491</td><td>148.26</td><td>Justin</td><td>987.0801425</td><td>Derek</td><td>12</td><td>2022</td></tr><tr><td>Derek</td><td>1056.868747</td><td>126.12</td><td>Pfeff</td><td>934.3839613</td><td>Derek</td><td>13</td><td>2022</td></tr><tr><td>Derek</td><td>1068.799009</td><td>166.38</td><td>Eddie</td><td>1043.339021</td><td>Derek</td><td>14</td><td>2022</td></tr><tr><td>Derek</td><td>1089.834797</td><td>143.08</td><td>Eddie</td><td>1025.980693</td><td>Derek</td><td>16</td><td>2022</td></tr><tr><td>Derek</td><td>1103.420452</td><td>75.42</td><td>Nick</td><td>1034.582526</td><td>Nick</td><td>17</td><td>2022</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 63
        },
        {
            "cell_type": "markdown",
            "source": [
                "Here's the less interesting, least volitile seasons"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "50ed2b70-35de-423f-b185-4c9abd4c2da8"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, MIN(ffmr), MAX(ffmr), MAX(ffmr) - MIN(ffmr), season\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team, season\r\n",
                "ORDER BY MAX(ffmr) - MIN(ffmr)\r\n",
                "LIMIT 10"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "dd8352c8-49be-4789-82c8-b9ad9e42a361",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(10 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.004"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 27,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "MIN(ffmr)"
                                    },
                                    {
                                        "name": "MAX(ffmr)"
                                    },
                                    {
                                        "name": "MAX(ffmr) - MIN(ffmr)"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Pfeff",
                                    "1": "992.1080077",
                                    "2": "1026.135904",
                                    "3": "34.02789629999995",
                                    "4": "2019"
                                },
                                {
                                    "0": "Nick",
                                    "1": "946.6285413",
                                    "2": "984.8730332",
                                    "3": "38.24449189999996",
                                    "4": "2019"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "1020.937091",
                                    "2": "1063.674546",
                                    "3": "42.737454999999954",
                                    "4": "2019"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "999.4774232",
                                    "2": "1043.339021",
                                    "3": "43.86159780000003",
                                    "4": "2022"
                                },
                                {
                                    "0": "John",
                                    "1": "1066.536098",
                                    "2": "1112.853612",
                                    "3": "46.317514000000074",
                                    "4": "2021"
                                },
                                {
                                    "0": "John",
                                    "1": "1077.016372",
                                    "2": "1123.640596",
                                    "3": "46.62422399999991",
                                    "4": "2022"
                                },
                                {
                                    "0": "Shev",
                                    "1": "942.9003157",
                                    "2": "989.9356585",
                                    "3": "47.03534280000008",
                                    "4": "2020"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "949.1485437",
                                    "2": "996.9431295",
                                    "3": "47.79458580000005",
                                    "4": "2021"
                                },
                                {
                                    "0": "Derek",
                                    "1": "978.1331",
                                    "2": "1026.091202",
                                    "3": "47.95810200000005",
                                    "4": "2019"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "979.5411632",
                                    "2": "1027.866558",
                                    "3": "48.32539479999991",
                                    "4": "2018"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>MIN(ffmr)</th><th>MAX(ffmr)</th><th>MAX(ffmr) - MIN(ffmr)</th><th>season</th></tr><tr><td>Pfeff</td><td>992.1080077</td><td>1026.135904</td><td>34.02789629999995</td><td>2019</td></tr><tr><td>Nick</td><td>946.6285413</td><td>984.8730332</td><td>38.24449189999996</td><td>2019</td></tr><tr><td>Eddie</td><td>1020.937091</td><td>1063.674546</td><td>42.737454999999954</td><td>2019</td></tr><tr><td>Eddie</td><td>999.4774232</td><td>1043.339021</td><td>43.86159780000003</td><td>2022</td></tr><tr><td>John</td><td>1066.536098</td><td>1112.853612</td><td>46.317514000000074</td><td>2021</td></tr><tr><td>John</td><td>1077.016372</td><td>1123.640596</td><td>46.62422399999991</td><td>2022</td></tr><tr><td>Shev</td><td>942.9003157</td><td>989.9356585</td><td>47.03534280000008</td><td>2020</td></tr><tr><td>Pfeff</td><td>949.1485437</td><td>996.9431295</td><td>47.79458580000005</td><td>2021</td></tr><tr><td>Derek</td><td>978.1331</td><td>1026.091202</td><td>47.95810200000005</td><td>2019</td></tr><tr><td>Pfeff</td><td>979.5411632</td><td>1027.866558</td><td>48.32539479999991</td><td>2018</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 27
        },
        {
            "cell_type": "markdown",
            "source": [
                "**Strength of Schedule**"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "2221b94f-0a29-4ad0-9a76-745c1f9ebab1"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, AVG(opponent_ffmr)\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team \r\n",
                "ORDER BY AVG(opponent_ffmr) DESC"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "c85c4cdf-7e1e-4f6a-a4b7-6bcf440b5644"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(13 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.008"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 75,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "AVG(opponent_ffmr)"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Eddie",
                                    "1": "1011.787121"
                                },
                                {
                                    "0": "Nate",
                                    "1": "1008.3220809026313"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1007.7721976500005"
                                },
                                {
                                    "0": "Zach",
                                    "1": "1007.45525259375"
                                },
                                {
                                    "0": "Sean",
                                    "1": "1006.3285160500001"
                                },
                                {
                                    "0": "Loof",
                                    "1": "1005.0905494083332"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "1004.9645384233768"
                                },
                                {
                                    "0": "James",
                                    "1": "1004.9053432200001"
                                },
                                {
                                    "0": "Nick",
                                    "1": "1003.8885925582277"
                                },
                                {
                                    "0": "Pete",
                                    "1": "1002.9222725068967"
                                },
                                {
                                    "0": "Shev",
                                    "1": "998.2378342090906"
                                },
                                {
                                    "0": "Justin",
                                    "1": "997.5591832623379"
                                },
                                {
                                    "0": "John",
                                    "1": "996.8494207513154"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>AVG(opponent_ffmr)</th></tr><tr><td>Eddie</td><td>1011.787121</td></tr><tr><td>Nate</td><td>1008.3220809026313</td></tr><tr><td>Derek</td><td>1007.7721976500005</td></tr><tr><td>Zach</td><td>1007.45525259375</td></tr><tr><td>Sean</td><td>1006.3285160500001</td></tr><tr><td>Loof</td><td>1005.0905494083332</td></tr><tr><td>Pfeff</td><td>1004.9645384233768</td></tr><tr><td>James</td><td>1004.9053432200001</td></tr><tr><td>Nick</td><td>1003.8885925582277</td></tr><tr><td>Pete</td><td>1002.9222725068967</td></tr><tr><td>Shev</td><td>998.2378342090906</td></tr><tr><td>Justin</td><td>997.5591832623379</td></tr><tr><td>John</td><td>996.8494207513154</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 75
        },
        {
            "cell_type": "markdown",
            "source": [
                "Hardest seasons:"
            ],
            "metadata": {
                "azdata_cell_guid": "ff76b5f4-e676-43dc-832e-31eb60267a65"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, AVG(opponent_ffmr), season\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team, season \r\n",
                "ORDER BY AVG(opponent_ffmr) DESC\r\n",
                "LIMIT 5"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "35ec5202-a644-4a77-8cb5-6c86d8ab58b4"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(5 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.011"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 80,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "AVG(opponent_ffmr)"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Nate",
                                    "1": "1025.33055928125",
                                    "2": "2021"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "1025.1246410294118",
                                    "2": "2022"
                                },
                                {
                                    "0": "Derek",
                                    "1": "1024.9846916333333",
                                    "2": "2020"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "1023.1421816687499",
                                    "2": "2020"
                                },
                                {
                                    "0": "Nate",
                                    "1": "1023.0055554600001",
                                    "2": "2019"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>AVG(opponent_ffmr)</th><th>season</th></tr><tr><td>Nate</td><td>1025.33055928125</td><td>2021</td></tr><tr><td>Eddie</td><td>1025.1246410294118</td><td>2022</td></tr><tr><td>Derek</td><td>1024.9846916333333</td><td>2020</td></tr><tr><td>Eddie</td><td>1023.1421816687499</td><td>2020</td></tr><tr><td>Nate</td><td>1023.0055554600001</td><td>2019</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 80
        },
        {
            "cell_type": "markdown",
            "source": [
                "Easiest seasons: (Justin is the commishiner, seems a bit fishy to me)"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "b5cc1e78-31d6-4d78-9c7f-15557121e475"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, AVG(opponent_ffmr), season\r\n",
                "FROM elo.timeline\r\n",
                "GROUP BY team, season \r\n",
                "ORDER BY AVG(opponent_ffmr)\r\n",
                "LIMIT 5"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "7e10fd43-4691-44f5-80cb-c9f3e5aa7e54"
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(5 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.011"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 81,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "AVG(opponent_ffmr)"
                                    },
                                    {
                                        "name": "season"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Justin",
                                    "1": "986.8627903624999",
                                    "2": "2022"
                                },
                                {
                                    "0": "Justin",
                                    "1": "987.38161545",
                                    "2": "2018"
                                },
                                {
                                    "0": "John",
                                    "1": "988.1944476466667",
                                    "2": "2019"
                                },
                                {
                                    "0": "John",
                                    "1": "990.4062408187499",
                                    "2": "2022"
                                },
                                {
                                    "0": "Nate",
                                    "1": "991.25694905",
                                    "2": "2018"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>AVG(opponent_ffmr)</th><th>season</th></tr><tr><td>Justin</td><td>986.8627903624999</td><td>2022</td></tr><tr><td>Justin</td><td>987.38161545</td><td>2018</td></tr><tr><td>John</td><td>988.1944476466667</td><td>2019</td></tr><tr><td>John</td><td>990.4062408187499</td><td>2022</td></tr><tr><td>Nate</td><td>991.25694905</td><td>2018</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 81
        },
        {
            "cell_type": "markdown",
            "source": [
                "Number of matchups vs 1100+ rated opponents: (Note that Derek hasn't had one even tho he's been in the league for a full 5 years)"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "c240ad3e-5e7a-4cff-89ff-6d9967df611b"
            },
            "attachments": {}
        },
        {
            "cell_type": "code",
            "source": [
                "SELECT team, COUNT(team)\r\n",
                "FROM elo.timeline\r\n",
                "WHERE opponent_ffmr > 1100\r\n",
                "GROUP BY team"
            ],
            "metadata": {
                "language": "sql",
                "azdata_cell_guid": "c560afe9-cece-4734-9042-4042815d063a",
                "tags": []
            },
            "outputs": [
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "(9 row(s) affected)"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "display_data",
                    "data": {
                        "text/html": "Total execution time: 00:00:01.002"
                    },
                    "metadata": {}
                },
                {
                    "output_type": "execute_result",
                    "execution_count": 77,
                    "data": {
                        "application/vnd.dataresource+json": {
                            "schema": {
                                "fields": [
                                    {
                                        "name": "team"
                                    },
                                    {
                                        "name": "COUNT(team)"
                                    }
                                ]
                            },
                            "data": [
                                {
                                    "0": "Sean",
                                    "1": "3"
                                },
                                {
                                    "0": "Eddie",
                                    "1": "6"
                                },
                                {
                                    "0": "Nate",
                                    "1": "9"
                                },
                                {
                                    "0": "Pfeff",
                                    "1": "3"
                                },
                                {
                                    "0": "Nick",
                                    "1": "4"
                                },
                                {
                                    "0": "Shev",
                                    "1": "3"
                                },
                                {
                                    "0": "Loof",
                                    "1": "3"
                                },
                                {
                                    "0": "Justin",
                                    "1": "4"
                                },
                                {
                                    "0": "John",
                                    "1": "2"
                                }
                            ]
                        },
                        "text/html": "<table><tr><th>team</th><th>COUNT(team)</th></tr><tr><td>Sean</td><td>3</td></tr><tr><td>Eddie</td><td>6</td></tr><tr><td>Nate</td><td>9</td></tr><tr><td>Pfeff</td><td>3</td></tr><tr><td>Nick</td><td>4</td></tr><tr><td>Shev</td><td>3</td></tr><tr><td>Loof</td><td>3</td></tr><tr><td>Justin</td><td>4</td></tr><tr><td>John</td><td>2</td></tr></table>"
                    },
                    "metadata": {}
                }
            ],
            "execution_count": 77
        }
    ]
}