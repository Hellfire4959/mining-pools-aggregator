    # Mining pool list aggregator

    **Hellfire4959's fork** of [ilmoi/mining-pools-aggregator](https://github.com/ilmoi/mining-pools-aggregator). The project combines source lists into domain, IP, CIDR and hosts-file outputs. This fork retains the inherited source code and list data; existing files are a historical snapshot, not newly verified detections.

    ## Use existing outputs

    | File | Contents |
    | --- | --- |
    | [lists/tlds.txt](lists/tlds.txt) | Aggregated top-level domain entries |
    | [lists/urls.txt](lists/urls.txt) | Domain entries including subdomains |
    | [lists/ips.txt](lists/ips.txt) | IP addresses |
    | [lists/cidrs.txt](lists/cidrs.txt) | Network ranges |
    | [hosts/hosts](hosts/hosts) | Hosts-file entries mapped to `0.0.0.0` |

    Review the source and freshness of a list before using it in filtering. A mining-pool entry describes a category; it is not, by itself, a maliciousness verdict. Line counts in the original documentation refer to its historical run.

    ## Rebuild the lists

    The inherited project uses Python 3 and Pipenv; dependencies are defined in [Pipfile](Pipfile) and its lockfile.

    ```bash
    git clone https://github.com/Hellfire4959/mining-pools-aggregator.git
    cd mining-pools-aggregator
    python -m pip install pipenv
    pipenv install
    bash refresh.sh
    ```

    `refresh.sh` retrieves configured sources, resolves domains and rewrites generated lists. It needs network access and may take time; legacy dependencies and external source availability can affect a fresh run. The cleanup did not perform a network refresh of the lists.

    ## Repository map

    | Path | Role |
    | --- | --- |
    | [blacklists/](blacklists/) | Source lists and generated IP-source lists |
    | [whitelists/](whitelists/) | Entries removed during aggregation |
    | [excluded/](excluded/) | Sources excluded by the original project |
    | [generate_lists.py](generate_lists.py) | Combine, subtract, deduplicate and sort lists |
    | [generate_ips_from_lists.py](generate_ips_from_lists.py) | Resolve generated domain lists |
    | [generate_hosts.py](generate_hosts.py) | Build hosts-file output |
    | [helpers.py](helpers.py) | Shared parsing and aggregation logic |
    | [UPSTREAM_README.md](UPSTREAM_README.md) | Original instructions and historical example output |

    ## Extend or contribute

    Add entries to the existing custom blacklist/whitelist files. Follow the source-file conventions in the original README when adding a URL-backed source. Keep attribution with new lists and submit a pull request with the expected output differences. Official upstream changes belong in the upstream project's process.

## Credits

All the credit goes to the folk who put together the original lists. This is merely an aggregator.

Ordered alphabetically:

- [andoniaf/mining-pools-list](https://github.com/andoniaf/mining-pools-list)
- [anudeepND/blacklist](https://github.com/anudeepND/blacklist)
- [codingo/Minesweeper](https://github.com/codingo/Minesweeper/)
- [eladmen](https://www.catonetworks.com/blog/the-crypto-mining-threat)
- [firebog](https://firebog.net/)
- [hoshsadiq/adblock-nocoin-list](https://github.com/hoshsadiq/adblock-nocoin-list)
- [Marfjeh/coinhive-block](https://github.com/Marfjeh/coinhive-block)
- [ZeroDot1/CoinBlockerLists](https://gitlab.com/ZeroDot1/CoinBlockerLists)
