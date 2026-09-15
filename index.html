import streamlit as st
import pandas as pd

st.set_page_config(
    page_title="서울 100년 기온 변화",
    page_icon="🌡️",
    layout="wide",
)

DATA_URL = "https://raw.githubusercontent.com/greatsong/modudata/main/data/seoul.csv"


@st.cache_data
def load_data():
    df = pd.read_csv(DATA_URL, encoding="utf-8-sig")

    df["날짜"] = pd.to_datetime(df["날짜"], errors="coerce")
    df["평균기온"] = pd.to_numeric(df["평균기온"], errors="coerce")

    df = df.dropna(subset=["날짜", "평균기온"]).copy()
    df["연도"] = df["날짜"].dt.year

    return df


st.title("🌡️ 서울의 100년 기온 변화")
st.write("서울의 일별 기온 데이터를 연도별 평균으로 집계하여 장기적인 기온 변화를 보여줍니다.")

try:
    df = load_data()

    # 연도별 평균기온 계산
    yearly_temp = (
        df.groupby("연도", as_index=False)["평균기온"]
        .mean()
        .rename(columns={"평균기온": "연평균기온"})
    )

    # 100년 단위로 보기
    max_year = yearly_temp["연도"].max()
    start_year = max_year - 99

    yearly_temp = yearly_temp[
        (yearly_temp["연도"] >= start_year)
        & (yearly_temp["연도"] <= max_year)
    ].copy()

    if yearly_temp.empty:
        st.error("표시할 기온 데이터가 없습니다.")
    else:
        col1, col2, col3 = st.columns(3)

        with col1:
            st.metric(
                "분석 기간",
                f"{yearly_temp['연도'].min()}~{yearly_temp['연도'].max()}년",
            )

        with col2:
            st.metric(
                "가장 낮은 연평균",
                f"{yearly_temp['연평균기온'].min():.1f} °C",
            )

        with col3:
            st.metric(
                "가장 높은 연평균",
                f"{yearly_temp['연평균기온'].max():.1f} °C",
            )

        st.subheader("연도별 연평균 기온")

        chart_data = yearly_temp.set_index("연도")[["연평균기온"]]

        st.line_chart(
            chart_data,
            y="연평균기온",
            x_label="연도",
            y_label="평균기온 (°C)",
            use_container_width=True,
        )

        st.caption(
            "※ 각 연도의 일별 평균기온을 평균하여 연평균 기온을 계산했습니다."
        )

        with st.expander("연도별 데이터 보기"):
            display_df = yearly_temp.copy()
            display_df["연평균기온"] = display_df["연평균기온"].round(2)
            st.dataframe(
                display_df,
                hide_index=True,
                use_container_width=True,
            )

except Exception as e:
    st.error("데이터를 불러오는 중 문제가 발생했습니다.")
    st.exception(e)
