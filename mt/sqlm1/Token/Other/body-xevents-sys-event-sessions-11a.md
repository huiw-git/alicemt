<Token xmlns:xlink="http://www.w3.org/1999/xlink"><maml:table xmlns:maml="http://ddue.schemas.microsoft.com/authoring/2003/5">
      <maml:thead>
        <maml:tr>
          <maml:TD>
            <maml:para>Column name</maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Data type</maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Description</maml:para>
          </maml:TD>
        </maml:tr>
      </maml:thead>
      <maml:tbody>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>event_session_id</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>int</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The unique ID of the event session. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>name</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>sysname</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The user-defined name for identifying the event session. <maml:notLocalizable><maml:literal>name</maml:literal></maml:notLocalizable> is unique. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>event_retention_mode</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>nchar(1)</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Determines how event loss is handled. Is one of the following:</maml:para>
            <maml:list class="bullet">
              <maml:listItem>
                <maml:para>S. Maps to <maml:notLocalizable><maml:literal>event_retention_mode_desc</maml:literal></maml:notLocalizable> = ALLOW_SINGLE_EVENT_LOSS</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>M. Maps to <maml:notLocalizable><maml:literal>event_retention_mode_desc</maml:literal></maml:notLocalizable> = ALLOW_MULTIPLE_EVENT_LOSS</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>N. Maps to <maml:notLocalizable><maml:literal>event_retention_mode_desc</maml:literal></maml:notLocalizable> = NO_EVENT_LOSS</maml:para>
              </maml:listItem>
            </maml:list>
            <maml:para>The default is S. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>event_retention_mode_desc</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>sysname</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Describes how event loss is handled. Is one of the following:</maml:para>
            <maml:list class="bullet">
              <maml:listItem>
                <maml:para>ALLOW_SINGLE_EVENT_LOSS. Events can be lost from the session. Single events are dropped only when all event buffers are full. Losing single events when buffers are full allows for acceptable <maml:token>ssNoVersion</maml:token> performance characteristics, while minimizing the loss in the processed event stream.</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>ALLOW_MULTIPLE_EVENT_LOSS. Full event buffers can be lost from the session. The number of events lost depends on the memory size allocated to the session, the partitioning of the memory, and the size of the events in the buffer. This option minimizes performance impact on the server when event buffers are quickly filled. However, large numbers of events can be lost from the session.</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>NO_EVENT_LOSS. No event loss is allowed. This option ensures that all events raised are retained. Using this option forces all the tasks that fire events to wait until space is available in an event buffer. This may lead to detectable performance degradation while the event session is active.</maml:para>
              </maml:listItem>
            </maml:list>
            <maml:para>The default is ALLOW_SINGLE_EVENT_LOSS. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>max_dispatch_latency</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>int</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The amount of time, in milliseconds, that events will be buffered in memory before they are served to session targets. Valid values are from 1 to 2147483648, and -1. A value of -1 indicates that dispatch latency is infinite. Is nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>max_memory</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>int</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The amount of memory allocated to the session for event buffering. The default value is 4 MB. Is nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>max_event_size</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>int</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The amount of memory set aside for events that do not fit in event session buffers. If <maml:notLocalizable><maml:literal>max_event_size</maml:literal></maml:notLocalizable> exceeds the calculated buffer size, two additional buffers of <maml:notLocalizable><maml:literal>max_event_size</maml:literal></maml:notLocalizable> are allocated to the event session. Is nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>memory_partition_mode</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>nchar(1)</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>The location in memory where event buffers are created. <maml:notLocalizable><maml:literal>memory_partition_mode</maml:literal></maml:notLocalizable> is one of:</maml:para>
            <maml:list class="bullet">
              <maml:listItem>
                <maml:para>G - NONE</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>C - PER_CPU </maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>N - PER_NODE </maml:para>
              </maml:listItem>
            </maml:list>
            <maml:para>The default partition mode is G. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>memory_partition_mode_desc</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>sysname</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Is one of the following:</maml:para>
            <maml:list class="bullet">
              <maml:listItem>
                <maml:para>NONE. A single set of buffers are created within a SQL Server instance.</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>PER_CPU. A set of buffers is created for each CPU.</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>PER_NODE. A set of buffers is created for each non-uniform memory access (NUMA) node.</maml:para>
              </maml:listItem>
            </maml:list>
            <maml:para>The default is NONE. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>track_causality</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>bit</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Enable or disable causality tracking. If set to 1 (ON), tracking is enabled and related events on different server connections can be correlated. The default setting is 0 (OFF). Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
        <maml:tr>
          <maml:TD>
            <maml:para>
              <maml:notLocalizable>
                <maml:literal>startup_state</maml:literal>
              </maml:notLocalizable>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>
              <maml:languageKeyword>bit</maml:languageKeyword>
            </maml:para>
          </maml:TD>
          <maml:TD>
            <maml:para>Value determines whether or not session is started automatically when the server starts. Is one of:</maml:para>
            <maml:list class="bullet">
              <maml:listItem>
                <maml:para>0 (OFF). The session does not start when the server starts.</maml:para>
              </maml:listItem>
              <maml:listItem>
                <maml:para>1 (ON). The event session starts when the server starts.</maml:para>
              </maml:listItem>
            </maml:list>
            <maml:para>The default is 0. Is not nullable.</maml:para>
          </maml:TD>
        </maml:tr>
      </maml:tbody>
    </maml:table></Token>